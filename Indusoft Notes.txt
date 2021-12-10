		Indusoft/HMI Startup
		
If Indusoft Target Path is incorrect, open file browse with the "..." button and click the Drive drop down.  Change the Disk and then it will show paths to update the target path.  Choose the correct path and download the project.
		
- To have a PLC tag "generated" into the Symbol file that gets imported into Indusoft, the tag must be declared within the   User Data Type Out_To_ICxx (udt_UIcommon_Output_[date here].)  
- If used specifically in a fixture or device, it can be defined within its that devices own UDT ie. (udt_FixXX_Output_Image, udt_PDxx_Image_[date here], udt_EOATxx_Image_[date here].)

Generating Tag into Symbol File and Import Into Indusoft
	1. Declare the tag within one of the UDTs defined above using the correct naming scheme and proper data type
	2. Once declared within the UDT, re-build the PLC which will generate a new Symbol file (Click Save once re-build is done)
	3. Now remove all other In_From_IC[x] and Out__To_IC[x] that are not the IC number you are importing the symbol file to.
	4. Once the new Symbol file has been saved, you can now Open Indusoft Version 7.X - NOT Version 8.X
	5. Within Indusoft 7.X on the "Home" tab click the "Import Wizard" which will Open a new window.
	6. In the Import Wizard window click "TwinCAT PLC Database" and click Next
	7. Verify "Do not import duplicate tags"  and Port 801 are selected , then select the Symbol file from the PLC folder, put {Target_PLC_Address} in the address field, as this will be manually overwritten in the tag's "MAIN DRIVER SHEET"
		- Note:  By default the file type is .tpy this is not the correct file type, it must be changed to .sym
	8. Once all the fields have been filled to Step 6's specifications click Next and verify the tags you are importing are in the list, then click Next to start the tag import  (This will start a progress window which will hang and seemed crashed, it isn't)
	9. Once the import progress windows say it has completed, you can now Open the Indusoft Project back within Indusoft Version 8.X
	10. Once back in Indusoft Version 8.X go to the TwinCAT Driversheet and scroll to the bottom to find your newly added tags.  To have them correctly communicate you need to copy "{Target_PLC_Address}" from another working tag and put that into the Address field of every new tag.  Then save this driver sheet and download the entire Indusoft project to the IC
	11. You have now successfully added new tags into the Indusoft project, BUT now you need to link those tags within the PLC so the screen will receive updates - GO TO -> Passing internal PLC variables out to IC



Troubleshooting Notes:
- If Security System cannot be started or errors similar to this , Open ICxx.APP file in note pad and delete line with "ConfigurationFlags" in it, then save.
  Also Overwrite tagl.bin, tagl.bin_autobck, taglex.bin, and taglex.bin_autobck (these are files associated with the Security system and Users)     


Passing internal PLC variables out to IC
	1. Passing an internal PLC variable out to the IC can be done in specific locations in the PLC framework based on the device the variable is specific to Examples Below:
		- Example -> Out_To_ICxx.T1_Zone_Test_ACK:= Safety_Zone_Test;
			- Out_To_ICxx.T1_Zone_Test_ACK is the variable on the side that goes out to the IC - declared in PLC within udt_UIcommon_Output_[date here] (on the Data Type tab in TwinCAT PLC Control)
			- Safety_Zone_Test is the internal PLC variable being used within the PLC logic - declared in the declaration field in the top window of MAIN Program (on the POUs tab in TwinCAT PLC Control)
		- Example 2 -> Discrete_Image.N00:= N00;
			- Discrete_Image.N00 is the variable on the side that goes out to the IC - declared in PLC within FixXX_Output_Image UDT (on the Data Type tab in TwinCAT PLC Control)
			- N00 is the internal PLC variable being used within the Fix01 PLC Program - declared in the declaration field in the top window of Fix01 Program (on the POUs tab in TwinCAT PLC Control)
	2. Once the variable has been declared within the correct Discrete Image/UI UDT and passed through in PLC logic, the only other factor that will prevent the tag from updating is if the tag has not been imported into the IC's tag driver sheet correctly - GO TO ->   Generating Tag into Symbol File

Modifying Symbol File for Each ICxx

1. In Beckhoff PLC, you must "Re-build All" to generate a new Symbol file for us to import into Indusoft 7.X.
2. Open the .SYM file in text editor application and remove all ".In_From_IC[X]" and all ".Out_To_IC[X]" with the number in the square brackets that DO NOT match your IC number.  After doing this, the symbol file is ready for import into Indusoft.
	- Example: Importing Tags into IC03 - Remove all tags with 1,2,4,5,6,7,8 in the square brackets on In_From and Out_To ICxx tags


Copy Indusoft Screen Updates "Happily"
This prevents the issue of flashing indicators not working until each screen is downloaded manually/individually

1. Update all required screens on IC01. 
2. Without Verifying Project, copy all 3 files of updated screens and overwrite existing files on IC to be updated. (Windows File Explorer) 
3. Verify Project on IC that is being updated (without removing temporary files.) 
4. Download updated screens to IC.

Create Persistent Tags

1. Find the tag(s) you would like to have retain their data when not being used or after project stoppage in the Project Tag list (Datasheet View) within Indusoft Development software.
2. Right click the tag list, click more columns, and select "Retentive Value."  This will show a new column to enable/disable retentive values for each tag in the list.
3. Now click the check box on the tags required, then save the tag list and download the project.
4. Finally reboot the IC to finalize the change.  (Without this step the tags do not operate correctly)

Tag Driversheet Troubleshooting Tools

There are several useful tools for finding which tag is causing the failure of a (request for all tags on a Standard driver shee Read Groupt) or a Virtual Read Group (request for a set of tags from a configured Main driver sheet or Tag Integration “hidden” Main Driver Sheet, shown in log as Read Block) to fail with an ‘invalid tag’ or other error.  Note: A ‘Timeout’ error means there was no response from the controller for a specific request, and indicates a Station field (device ID) issue or a network issue,  not a ‘bad’ tag.

The first tool depends on the driver you are using, but most of them will support the feature wherein you enable the Protocol Analyzer setting on the Output Window along with the Field Read Commands setting, and if the read fails, the Output Window will provide the name of the first ‘bad’ tag found in the group which caused it to fail. For each group read, the Output Window will display in sequence the request data (prefixed by the characters Tx) sent by IWS, then the response data (Prefixed by Rx) sent by the controller, and then the results of the request/response, which is the Read Group (SDS) or Read Block (MDS) line that contains the error message, and this will then be followed by an extra line that explicitly provides the name of the first tag in the requested group that the controller was unable to find. If only one tag in that group had an issue, and it is removed from the request (or the entry for the tag was corrected in terms of syntax, spelling, etc.) then the group read will succeed on the next scan. If more than one tag in the failed group had an issue, and the first was removed or corrected, then the next ‘bad’ tag name would be reported on the next scan of that group.

The second tool is used to identify which tags belong to a given Virtual Read Group created by a configured Main Driver Sheet or by the hidden Main Driver Sheet that is created when using Tag Integration. In either case, you can edit the App file of the project to include the ‘DumpDriverSheets’ line in the [Options] section. There will almost assuredly be an [Options] section already, in which case you simply add the line, but if not add the section heading ‘[Options]’ as well.



!!! SEE IC SETUP GUIDE FOR MORE INFO!!!
