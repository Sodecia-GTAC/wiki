# Beckhoff

### Important Side-notes
- Download To PLC/Upload From PLC
- Our I/O = PNP(Sourcing) Not NPN(Sinking)

### XAE compiler check boxes
- If you find you have unusual / unexpected errors and / or warnings during a build check the Compiler Warnings
- Find by right clicking the _PLC Project ("SODGxx_SSCC601_xxxxxxx_PLC Project" as example), then navigating to Compiler Wanrings
- Be sure the following are delselected (unchecked): C0195, C0196, C0197, C0198, C0327
- All others should be left selected (checked)

![Example](./Images/XAE%20Checkboxes.jpg)

---
## Addressing

### ICxx Addressing

- (reference of EL1904 picture)
- High Byte
- Low Byte
- Low Bit - High Bit

- IC01.T02-T09, T11, T12 - 610-617, 618, 619
- IC02.T02-T09, T11, T12 - 620-627, 628, 629
- IC03.T02-T09, T11, T12 - 630-637, 638, 639

---

### STxx Addressing
S2 - x1 Value  
S3 - x10 Value  

---  

### STxx Address Example
- S3 - 2 x10
- S2 - 3 x1
- Address = 23

Navigate to (Profibus) Customer Interface on Emhart/Stanley/Tucker Welder
Programming > System Configuration > Customer Interface Configuration > CI Configuration > Connection Parameter and Status > Profibus

---

### Rxx Addressing
- Rxx.T02 = 10*(Robot #)
- Rxx.T03 = 10*(Robot #) + 1
- Rxx.T04 = 10*(Robot #) + 2

---

### Rxx Address Examples
- R01.T02 (EL6900) - 10
- R01.T03 (EL1904) - 11
- R02.T02 (EL6900) - 20
- R02.T03 (EL1904) - 21
- R09.T02 (EL6900) - 90
- R09.T03 (EL1904) - 91
- R21.T02 (EL6900) - 210
- R21.T03 (EL1904) - 211

---

### EP Block Address Settings
EP1908 (ESW) Address top dial as least significant bit (based on node being upright)
!! Requires a power cycle to update!! 

![EP Block Address Settings](./Images/EP%20Block%20Address%20Settings.png)

---

### System Manager

Make habit a of re-building the PLC and re-scanning the PLC in TwinCAT System Manager(TSM)

To start working with a controller, open the System Manager Config file and go to system tab. Click choose target, and then Search Ethernet. Click broadcast search, and pick controller then enter Admin password of HMI to add route.

If CRCs do not match OR devices are not reading statuses in System Manager -- Connect to local IP, then back to the target machine (refresh connection)

Every change made to safety or device configuration needs to be downloaded onto the controller through activating TSM project

On first connection to IC01 you must install the TwinCAT EtherCAT Driver
1. Open your system manager project the IC
2. Click I/O Devices>EtherCAT Master>Adapter(Tab)
3. Once on the Adapter Tab Click "Compatible Devices" Button
4. From the Compatible Devices Window click X108 (EtherCAT), then click Install and close this window
5. Click the "Search" Button and Select the X108 (EtherCAT) and Click OK and Save the System Manager
6. Generate Mappings, Check Config, and Activate Configuration
7. Now your project should be in Run Mode on the IC
8. After moving over to your development PC you must "Search" for the correct connection to get System Manager to go into Run Mode from development PC deployment

#### Setup AUTO Run Config/Verify Load Boot Project
For Configuration Auto Run go to: System - Configuration>Boot Settings(Target) and Enable Run Mode on Boot with the proper Administrator info then click apply (information provided in IC setup package)

- Verify PLC Task auto load Boot Project IS SELECTED: PLC - Configuration>PLC Settings (Target)>Boot Project -- CHECK the box beside 1. Run-Time System (Port: 801) then click Apply
- Verify PLC Task Load/Store Retain Data is NOT SELECTED: PLC - Configuration>PLC Settings (Target)>Load/Store Retain Data -- UNCHECK the box beside 1. Run-Time System (Port: 801) then click Apply

---

### SDxx Drive Notes:
- Drive Manager in SDxx tab menus will give diagnostic information about the error statuses of each channel on the drive (can also reset)
- Drive Manager in SDxx tab can "pull" motor and feedback information through clicking the "Scan feedback [SD#] / motor (this information is collected from the drive connected to the Channel)
- When getting servo drives running in safety, change the state of the STO_Mode_Active in the Safe Parameter tab (this may fix the status)

---

### System Manager Notes:
- When unable to append certain types of devices, verify which connection you are adding it to - Eg. Connection A, B, C, D (Port definitions below)
	- Also verify the correct XML files are within the lib folder for TwinCAT
- If EL6695 Connection keeps getting deleted, the XML file for it may need to be added to the TwinCAT/IO/EtherCAT folder
- If TSM gives the Error -> CAdsWatchServer: :AdsParseSymbol no more handles, try power cycling the IC to allow the memory to adjust to the new amount of symbols/tags
- If Broadcast Search is not finding your IC, verify the IP and Subnet Mask are correct
- If TwinSAFE FBs aren't receiving bits from decouples, re-scan PLC and download config again.  Also re download TwinSAFE group
- MasterMessage & FSoE's first status number should read '36' IF the addressing and communication is good
- If "PLC Task (FPU) invalid operation" most likely an issue with the hardware mapping to the PLC, make sure System Manager is up to date and re-scan PLC and Activate Configuration
- TwinCAT 3 - If System is not going into OP from SAFEOP without error, verify licensing

---

### Device State Errors
- VPRS -- means the device at that connection point does not match the configured device (Check Log Viewer)
	- VPRS = (Vendor ID/Product Code/Revision Number/Serial Number)
- INIT_ERR - means configured device parameters do not match actual device
- ERR PREOP - means device had issue going from PREOP to SAFEOP (check Log Viewer)
- ERR SAFEOP - means device had issue going from SAFEOP to OP (check Log Viewer)
- LNK_MIS - means communication is made on a connection that is not linked/defined
- LNK_ADD - means addition link has been made, but no connection detected
- LNK_ERR - means the connection is made without communication detected

---

### Port Definitions
Port A - Bus/Rail connection front/left
Port B - Port connection X1/top RJ45
Port C - Bus/Rail connection back/right
Port D - Port connection X2/bottom RJ45

---

### TwinSAFE
TwinSafe Login  
User: Administrator  
Serial: [copied from TwinSAFE tab]  
Pass: TwinSAFE  

!!!ALWAYS ACTIVATE CONFIGURATION AFTER DOWNLOAD TWINSAFE UPDATES!!!

!!!Standard Inputs can only be linked on an AND FB on AndIn1, no other FB or port support Standard Inputs!!! 

Get System Configuration good first - EVERYTHING IN OP - Disable anything that is Missing Link and Disconnect any devices that are disabled

TwinSAFE Connections are made automatically once I/O has been linked in TwinSAFE FBs

After TwinSAFE Connections are created, verify their Watchdog timers are set correctly

#### Normally Closed Inputs on FBs show inverted signal to actual input

1. Download safety FBs to each EL6900.
2. Comment Safety Reset IF "All_Estops_Off" IF Statement and add a line below it like so:  SAFETY_RESET;

This is used only initially to reset the 6900s before getting all device working.  Verify in Function Blocks on 6900s with issue that the Safety Reset is getting back to the Err_Ack when Toggling the bit.

3. If Com Errors exist use the EL6900 documentation to diagnose the Binary Diagnosis Value and solve the issue.
4. Clear all E-stops and EDM faults to get control power reset functioning and remove the SAFETY_RESET; line of code.

##### SGs_COM_ERR - Connection Issue
- Decoupled Comm Error means a connection issue to another device
- Function Block Comm Error means a connection issue within the local device
SGs_FB_ERR - Function Block Issue
- Function block has Error
SGs_COM_ERR - FB Output Issue
- Only on Safe Output Cards

---

### Generating Master/Slave Messages from Rxx to IC01 6900 Connections
1. Add TwinSAFE connections on the Master 6900 (IC01) as well as Master connection information in Robot Decouple Connection List, and then add TwinSAFE connections on Slave 6900 (Rxx) and Slave connection information in IC Decouple.
	- It is critical not to click anywhere within the Slave TwinSAFE connections tab when developing the 6900 connection, as it will delete the connection UNTIL it has been linked to another Master 6900.
2. Once the decouple connections are made on both ends, link the correct Message variable to link end to end (between IC01 Master and Rxx Slave) within Module 1 on the 6900s
	- ST_FSoE_02Byte is used for FSoE messages from/to robots
3. Once the messages are linked the links can now be made within decouples on each 6900.
In TC3 must be linked within the IO tree, NOT Safety

---

### FSoE Connection Info
- IC01 to R01 & R01 to IC01 FSoE Connection ID = 1xx + [10 x robot number] (same both ends)
- IC01 to R01 FSoE Address = [10 x robot number]
- R01 to IC01 FSoE Address = 6xx + [10 x robot number]
- Watchdog Timer is set to 250ms on both ends

---

### TwinSAFE Notes:
- If EL6695 Connection keeps getting deleted, the XML file for it may need to be added to the TwinCAT/IO/EtherCAT folder
- If TwinSAFE FBs aren't receiving bits from decouples, re-scan PLC and download config again.  Also re download TwinSAFE group
- An Rxx 6695's FSoE address will always show 0 within the PLC CoE - Online tab, verify this setting on the Safety Configuration on the Kuka HMI
- MasterMessages & FSoEs first status number should read '36' IF the addressing and communication is good
- Standard Inputs can only be linked on an AND FB on AndIn1
- EL1904s only need Sensor Test set "FALSE" & Logic of Input Pairs set to "any pulse repetition OSSD, sensor test deactivated (2)" when using light curtains on those safety inputs
	- These settings are found on each 1904 on the "Safe Parameter" tab
- Connecting a EP1918/EP1957/EL6910 (new series TwinSAFE Card) with another TwinSAFE Connection requires using the same TwinSAFE Address, which must be unique to any other address TwinSAFE address
    - Do not connect them to each others addresses the old school method, this does not work

---

## PLC
- Verify Source Code Download Implicit on Create Boot Project and All Files are checked in Project>Options>Source download
- Also Check Remind of boot project on exit in Project>Options>Load&Save
- F2 key to add in Function Blocks 
- Shift+F2 to add new FB/Variable in declaration and then F2 in PLC code to add the new FB/Var
- Add libraries in PLC Control>Resources>Library Manager>(right click library window, and click additional library)>(Find library to add and click OK)
- Everytime the PLC gets rescanned the System Config should also be re-activated
- When performing math with REAL variables, all other data must also be REAL or decimal places will be lost

---

### Setup GTAC Config

##### Robot Setup
- Remove unused robots
- Set correct Robot Type
- Configure accessories (Water Stand, MIG, EOAT, etc.)
- Establish Robot Interferences (Interlock Map)

##### I/O Linking
- Input advanced and retracted sensors from I/O map into clamp Function Blocks, as well as valve outputs and clamp fault bits
- Input sensor inputs into part present Function Blocks, and sensor fault bits

##### Fixture Setup
- Add/Remove clamps, pins, slides, nut checks, and sensors
- Create load, weld, unload, and sensor logic steps
- Setup valve logic
- Create robot to fixture re-positions

---

### Notes:
- Unload_Complete ONLY used for Robots, human unload is taken care of within Cycle_Complete
- PLC priority in unsafe order is a prompt that comes up on PLCs with two run-times.
- If getting Error 4020: "Operand must have write access" -> make sure the variable is declared within the program attempting to write to the variable OR declared as a VAR INPUT in that Program/Action.
- Using Bit 31 of ECAT Slave Cables Breaks causes all bit values TRUE and flashed every cable break
- If getting Error "Variable [var name here] too large for address [address position here]" -> run a Clean All & allow the TwinCAT configuration to "clear," it will re-map the links and change the memory positions
	- The specified variable has expanded in memory size but the current location does not have room to expand
		 
---

### Logic Examples

(*Load Complete w/ Repos*) 
Load_Complete:= All_Sensors_On.2
OR (Tool_At_Weld.0 AND All_Sensors_On.3)
OR (Repo_Reqs.0 AND All_Sensors_On.4)
OR (Repo_Reqs.1 AND All_Sensors_On.5)
OR (Repo_Reqs.2 AND All_Sensors_On.6)
OR (Repo_Reqs.3 AND All_Sensors_On.7)
OR Weld_Robots_WorkingOK
OR Welding_Complete;
 
(*Homing Unclamp Step*)
Unclamp_Step.X:= NOT Dry_Cycle AND Cycle_Complete AND NOT Tool_At_Home AND All_Sensors_Off;


---