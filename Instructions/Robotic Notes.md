# Robotic Notes

## KUKA

#### General Troubleshooting Tips

- Play/Run INI @ top of KUKA programs as first troubleshooting method

- With used robots reset safety configuration to defaults at start of commissioning.

-General Servo Error usually indicates incorrect voltage supply (verify transformer tapping)

- Compact Cabinet use X66 for laptop connection with WorkVisual 

- WorkVisual version can be found via file -> C/KRC/Roboter/Config/User/Common/KRC_IO.xml

- To Source TCP, Base Frame, Load Data, go to -> KRC\R1\System\config.dat

- For WorkVisual Tech Package compatibility warnings and build errors, go to  -- Extras/Options/Rules -> uncheck "prevent code generation....."

---

#### Kuka Relay Type
- Supports Aux Contact = 3RT2017-1FB42
- No Support for Aux Contact = 3RT2017-1KB42

---

#### Safety Monitoring Spaces on Human Zones
- by input
- protected space
- stop at boundaries
- T1 mode hides zone spaces, they are disabled when hidden
	- Enable T1 Zone Test to remove zone override with teach

---

#### Monitoring Space/Cell Perimeter Distances
- Monitoring Space Entrance Minimum = 1500mm OR 60" from Operator Fence
- Cell Space Wall (Human Zone) minimum = 900mm or 35" from LC beam
- Call Space Wall (Equipment Zone) minimum from Mesh Fence = 150mm or 6"
- Horizontal Light Curtain beam Distance from Floor Maximum = 300mm or 12"

---

#### Mastering Log
- Location - C:/KRC/ROBOTER/LOG/Mastery.log
- Can see the history of axis mastering

---

#### Axis Mastering Tips
- Requires 2 decimal places to be 0 in the second field (mm)
- on a KR210 putting A4 to +2°, should make finding the master position easier
  
---

#### Config Mon INI
- Need Expert Login to Access C:/
- ConfigMon.ini is located @ C:/KRC/User/ConfigMon.ini
- Setup for Variable Monitoring on Variable Overview Window on Robot

---

#### Turn ON KRC AUX Relays (Safe OP)
1. Login to Safety Maintenance Technician.
2. Go into Configuration>Safety Configuration
3. Click/Tap Hardware Options button on the front Safe Config screen.
4. Verify "Input Signal for Peripheral Contactor (US2)" is selected as "from KRC"
Safe OP must be operating to test these relays (Start-up mode bypasses Safe OP)

---

#### VT_Direct() Setup/Info
1. Login to Expert mode to gain access to editing programs
2. Open program that VT_Direct is being added to
3. Add VT_Direct() between two motion lines that the turns direction needs to be controlled within.
4. Using the VT_Direct description below add the correct points, base and tool frames from each point.
The subprogram VT_DIRECT calculates the status of axis 5 at the end point in such a way that axes 4 and 6 are moved as little as possible. The program requires the coordinates X, Y, Z, A, B and C of start and end points as well as the status of the start point.

---

#### VT_Direct Example
VT_Direct("StartPoint", "EndPoint", "StartPointBaseFrame", "EndPointBaseFrame", "StartPointToolFrame", "EndPointToolFrame")
	
	PTP P5 Vel=100% PDAT5 Tool[1]:GUN BASE[1]:FIX1
	
	 VT_Direct(XP5, XP6, base_data[1], base_data[2], tool_data[1], tool_data[2])  
	
	PTP P6 Vel=100% PDAT6 Tool[2]:GRIPPER BASE[2]:FIX2
	
Notes:
- if a point is entered with base_data[0] or tool_data[0], it should be entered as $nullframe instead, as tool and base data 0 do not exist

---

#### Gun Approximation Direction (Servo_TC)
1. Login to Expert Mode to gain access to all directories
2. Go to R1/TP/Servo_TC and open EG_ExternAuto 
3. Go to line ~40 and  change EG_DIRECTION_OF_TIPWEAR[x] from NZ > PZ or vice versa (x is the number of the external axis that is the gun)
4. Run a Cold Boot with Reload All Files to update the "boot files"
Gun Approximation Direction (ServoGunBasic)
- ONLY Changeable in WorkVisual (From my knowledge)

---

#### Change Maximum Tip Wear
1. Login to Expert Mode to gain access to all directories
2. Go to R1/TP/Servo_TC and open EG_ExternAuto
3. Go to line ~263 and change EG_WEAR_MAX[1] to desired maximum tip wear value.  DEFAULT=8mm
4. Run a Cold Boot with Reload All Files to update the "boot files"

---

#### Fix Gun Tip Wear E1+ Limit Error
1. Go into Display>Variable>Single and type EG_WEAR[x] (x = Ext gun #), and hit update. If the value displayed is higher than 8 then this is the reason of the error. 
2. Set the value of the variable to 0, and then Master the external axis at issue. 
3. Once the gun has been remaster, run tip wear and check the EG_WEAR[x] value. It should be very close to 0.

---

#### Increasing Weld Schedule Timeout
Display>Variable>Timer 13 is the schedule timer
1. Login to Expert Mode to have privilege's to write to variables. 
2. Open Display>Variable>Single
3. In the name field enter EG_TIMEOUT[2]
4. Update this value by entering a value in milliseconds within the "New Value" field. Default is 3000ms.
5. This is mainly needed for the tip dress schedule which can be up to 8 seconds long.

---

#### Servo_TC Option Package/Servo Gun Editor in
KUKA Work Visual Windows Application 
1. Open project in Work Visual
2. Activate project (must be activated) 
3. Highlight external drive (TS serial number)
4. Click Editor Tab on top bar
5. Click Option Packages in Editor Tab Menu
6. Click Servo Gun Editor

---

#### Decouple EXT Axis
1. Get Servo Tech on Status Keys (KUKA Menu>Configuration>Status Keys>ServoTech) 
2. Get Servo Power on Robot to Enable Status Key Functionality
3. Press Decouple of EXT Axis that is missing (3rd ServoTech page - gun icon with X through it)

---

#### Automatic Gun Calibration Tips
- Do automatic mastering first, 30mm space between movable and fixed shank (As specified by Kuka)

- DON'T USE WIZARD unless you are starting from scratch, it will zero all calibration data.  You must complete the full wizard and not do it partially.
  
- Turn of Sodecia SPS

- Shank Wear/Tip Wear should be reset/zero before doing gun calibration = SG_WEAR[x] and SG_TIPSEATING_MM[x] x= external axis

- Obara Max Flexion does not equate to Maximum Deflection (don't use Obara Deflection values)

- Applying 40% Torque and measuring the actual gun position can be used for  setting the 5 Pre-Calibration points by entering that position in the top field (IF automatic calibration is not working)

- Having the gun as a couple able axis could be a negative impact on the gun calibration as it changes the maximum safety velocity of E1 (E1 Speed must be 1500mm/s)

- For Max Flexion input 20mm, it will calculate itself during the automated process

- Opening Width = Gun @ 360 degrees, will automatically calculate spindle ratio

**If you get errors while doing gun calibration, you may need to reload all files/reboot**

---

#### Adjust External Axis Home Position Tolerance
1. Login to Expert User to get access to all directories
2. Deselect SPS to allow file modification
3. Go to KRC:\R1\Mada, then Open $machine.dat
4. After opening $machine.dat go to line ~588 (E6AXIS $H_POS_TOL= ), and then change each external axis in this line to the degree of tolerance you would like.  Save the file and reselect the SPS
5. Run a Cold Boot with Reload All Files to update the "boot files"

---

#### ASYNC_MODE Change
Changing this Mode switches whether Block Selection and T1 disables the Asynchronous Axis Selections
1. Login to Expert to get access to all directories. 
2. Deselect SPS to allow file modification. 
3. Go to KRC:\STEU\Mada and then Open $custom.dat
4. After opening $custom.dat go to line ~212 or ~75 and change $ASYNC_MODE from 'B0000' to 'B0010'
5. Run a Cold Boot with Reload All Files to update the "boot files"
Bit 1 controls Block Selection affect on ASYNC_MODE
Bit 0 enables control of ASYPTP motions in the SPS

**!!!External Axis with position monitoring in safety configuration must be mastered, they cannot be made asynchronous to ignore the external axis position on master test -- IF these position monitored axis are not needed for human safety then they can be monitored in SPS using User Outputs for interlocking with adjacent robots!!!**

---

#### ASYNC_AXIS Definition
- B'0001' = E1 Asynchronous  
- B'0010' = E2 Asynchronous  
- B'0100' = E3 Asynchronous  
- B'1000' = E4 Asynchronous  

---

#### Change Home Position Tolerance
1. Login to Expert User to get access to all directories
2. Go to KRC:\R1\Mada then Open $Machine.dat
3. Go to line ~590 and find $H_AXIS_TOL
4. Change appropriate external axis to 360 instead of 2 to have table axis OR servogun tolerance be 360 degrees
5. Close file and save

**This is necessary to get tip_wear program to maintain AT_HOME when running**

---

#### Ignore External Access for Master Reference
- Add ASYNC_AXIS = 'B0111' in both the Start and Back programs for MasRef_Main and it will pass no matter the position of the E1, E2, and E3
- NOTE - external axis must still be taught into master reference position with the 5 degree tolerance in mind 

---

#### Enable/Disable T2 Mode
1. Login to Expert User to get access to all directories
2. Go to C:\KRC\ROBOTER\Config\System\Common, then OPEN cabctrl.xml
3. After opening cabctrl.xml go to line ~59 and change OpModes T2="[off/on]," then save file. 
4. Run a Cold Boot with Reload All Files to update the "boot files"
5. Note you need to be logged in to use T2

---

#### Enable/Disable Brake Test (OLD FIX, no longer works correctly - 2021/10/07)
1. Login to Expert User to get access to all directories
2. Go to C:\KRC\ROBOTER\Config\User\Common\MotionDrivers, then OPEN motiondrv.ini
3. After opening motiondrv.ini verify the structure includes objects in example below, IF NOT then correct structure and save file.  Then reselect SPS.
4. Run a Cold Boot with Reload All Files to update the "boot files"
   
   ----------------motiondrv.ini File Example------------
   [BASE_DRIVER]
   
   [TOOL_DRIVER]
   
   [AXIS_DRIVER]
   
   [EMI_DRIVER]
   
   [FEEDFORWARD_DRIVER]
   
   [OTHER_DRIVER]
   BRAKE_TEST,mdrBrakeTest.o
   
   OLDC,loadDataDevice.o

---

#### Change $ROBROOT (Floor vs Ceiling Mounted Robot)
1. Login to Expert User to get access to all directories
2. Go to KRC:\R1\Mada then OPEN $machine.dat
3. Go to line ~95 and change $ROBROOT C value 0 for floor mount and 180 for ceiling mount
4. After changing this value, a "position deviation" error will occur. You must login to safety and acknowledge the change, and then download the safety.
5. Run a Cold Boot with Reload All Files to update the "boot files" 
Correct Issue with $OUT[150] turning on during weld fault
1. Login to Expert User to get access to all directories
2. Go to KRC:\R1\TP\Userfiles then OPEN SG_UserSRErrrToQuit.src
3. Go to line ~21 and comment out the line that has SGL_SetOut(150, valueOut)
4. Also comment the line that has SGL_SetOut(159, valueOut)
5. Close file to save changes
Correct "Weld Timer Communication Timeout" Message
1. Login to Expert User to get access to all directories
2. Go to KRC:R1\TP\ServoGun\WeldTimers\SG_TimerImplCustom
3. Go to line ~19 after "DECL BOOL NewStart and add or modify the following 2 lines of code
   SG_SetNumberToOutput(SG_ProgramNumber_WT_S[SG_ActiveWeldTimer],SG_ProgramNumber_WT_E[SG_ActiveWeldTimer],SG_ProgramNumber) ; WTC added line
   
   RETURN 1; WTC changed line from "RETURN -1"
   
4. Close file to save changes, and this should correct the issue immediately 

---

#### Teach EXT TCP
1. Select 5D calibration mode.
2. Choose EXT Tool/Base Frame number to be calibrated, and the TCP used to measure points. 
3. Bring the measuring TCP to the new TCP of the EXT Tool, to measure its TCP. 
4. Then align the EXT Tool +X coordinate pointing towards - Z of robot flange, with +Y of the robot flange facing upwards.  This determines the EXT Tool working direction.

To change which EXT Axis is selected press the number button on the same page as the Couple/Decouple buttons. 

---

#### Remove EXT gun from brake test

C/KRC/ROBOTER/Config/User/Common/Mada/MotionDrivers

mdrBrakeTest=63 NOT 127


#### Example of Folds in KRL (Kinetic Rule Language)

1. Create End Fold.
2. Setup Fold contents.
3. Create Start Fold with Specified Name.
(square brackets only for example....not needed for actual KRL fold)
```
	;FOLD [fold name here]

	[fold contents here]

	;ENDFOLD
```

#### Example of Jumps in a Motion Program
```
	GOTO JUMP

	PTP..... 
	PTP.....  

	OUT89

	JUMP:
```

(Jumps must be coded in an Open program, NOT a selected program.  Will create syntax errors.
Must establish jump label before writing jump command.)

---

#### Gun Open Distance Setting
Limit how much the gun opens before welding by setting the EG_MOVE_DIST to a lesser value than default (usually 1.) The lower the negative value the less the gun opens. Be cautious setting EG_MOVE_DIST lower, as this could cause movable shank to drive through fixed shank!!!

YOU MUST SET the value back to default value after the welds that require less gun opening distance.
```
EG_MOVE_DIST = -6


PTP SG14 Vel=100 % PDAT50 ProgNo=120 ServoGun=1 CONT=CLS OPN Part=2 mm Force=3.3 kN ApproxDist=5 mm SpotOffset=0 mm Tool[1]:GUN Base[2]:FIX04 

 8

EG_MOVE_DIST = 1
```

#### Preparing Kuka WoV Package for Robot Commission
- Clear All Interf Jobs except EquipInterf8
- Clear All Tool/Base Frames
- Safety Configurations
	- Default Monitoring Spaces
	- Zero/Clear Tool Spheres
	- Zero Cell Perimeter
	- Zero Master Reference Positions
	- E1 T1 Velocity = 1500mm/s
- Delete All Job Programs in Sodecia Folder
- Verify IF any additions were made during project, determine to remove OR keep


---

### ServoGun SG Init commands fail
		
Issue:
Encountered an issue with 2 robots on project 19017-9 where SG.INIT commands would cause an error message stating "The command force is lower than the switch-on threshold for force control", and would fail. This is caused by the force set for servogun init motions (squeezing after new caps) is set lower than some minimum that exisits within the controller. Somehow this number was changed internally from 2000 to 900. 

Solution:
Two values must be changed within the ServoGun files.
TP>ServoGun>SG_ConfigData_ServoGuns
~Line 27, Servogun[1] ForceInitNew value must be change to the appropriate value (in my case 2000)

TP>ServoGun>SG_Main
~Line 197, SG_ForceInitNew must be change to the appropriate value (in my case 2000)

### KRC4 Servo XM Connector Including Brake
		
Taken from....:


---

### Notes:
- If when opening a EL6900 TwinSAFE a connection is deleted. You need to get the EP6695prim & EP6695sec XML files in your C:/TwinCAT/Io/Ethercat folder
- If approximation not possible, run INI at top of program
- If archiving a robot is not able to successfully complete, you may need to delete excess work visual projects
- SION-CIB inputs 6&7 are for master reference switch (will differ on each cabinet type)
- Without Water Cooling for Welder, must be in Under Construction to Ignore COOL signal in WTC Raft
- If Robot's are looping brake test even after completing, verify the Sodecia PLC SPS file includes this line -----> $OUT[34] = $IN[34]    (passes internal status of brake test requirement to bit that triggers job call in PLC)
- If robot cannot run Tip Wear, check EG_Wear[x] (x = gun number), if the value is very high, reset to 0 in Variable/Single window
- If error "invalid module" when touching up a point, try changing the point and saving it with CMD OK.  This may allow it to be touched up after this
- VPRO-MAX3DKUKA is for WorkVisual, while VPRO-MAX3D is for the Controller
- SG_Lib, SG_Main, and SG_TimerImplCustom file are critical for welding correctly, when welding issues occur, verify these 3 files against known welding robots
- Any fans not operating at correct RPM will prevent robot motion
- Sealant Speed Recommendation - 0.15m/s
- If error "value assignment inadmissible" with ASYNC_AXIS command, may be possible program is opened in EDITOR mode "behind" PROGRAM mode, verify by opening program and closing, then select program and test

---
### WTC/RAFT
- CSTP (Control Stop) is from WTC Timer Internal Logic
- CS2 (Control Stop 2) is from Discrete Cable from KUKA Relays 
- TS2 is the Thermal Signal from the Welding Transformer
- COOL is from PLC for Waterstand Temp & Flow OK

Kuka EIP* = 192.168.100.1XX (XX = Robot Number)
*Set on Kuka HMI in Network Configuration
*Also Set on WorkVisual EtherNET IP Settings

Kuka WorkVisual *= 192.168.100.2xx (XX = Robot Number)
*Program in bus structure, EtherNetIP, WTC Gen6..

WTC EIP* = 192.168.100.2XX (XX = Robot Number)
WTC IP* = 192.168.1.2XX (XX = Robot Number)
*Set on WTC DEP or RAFT

WTC DEP Con1 Size:  Program Mode Button -> EIP Mapping/EIP Configuration/F5/F5/ -> change CON1 size from 02 to 04 in/out*
*Download and restart WTC. Must do for communication!!

#### Increasing Weld Schedule Timeout
1. Login to Expert Mode to have privileges to write to variables. 
2. Open Display>Variable>Single
3. In the name field enter EG_TIMEOUT[2]
4. Update this value by entering a value in milliseconds within the "New Value" field. Default is 3000ms.
5. This is mainly needed for the tip dress schedule which can be up to 8 seconds long.

---
### WORK VISUAL
		
- KLI Port is for programming connection & KONI Port is for internal KUKA network devices

- Before connecting to any robot with Work Visual, first verify the KUKA Option Package versions from your laptop to the robot. 

 -If any differences, update/downgrade to the version on the robot.

#### External Axis Configuration Info
- The motor does not determine the catalog file current rating
- The KPP/PowerPack supplying the motors determines the current rating for the catalog file
  
- HA64/40 is used for main axis of rotation on KP3s
- PA1/PA2 64/40 are used for the trunnion axis on KP3s

#### Servo_TC Option Package/Servo Gun Editor in KUKA Work Visual Windows Application 
1. Open project in Work Visual
2. Activate project (must be activated) 
3. Highlight external drive (TS serial number)
4. Click Editor Tab on top bar
5. Click Option Packages in Editor Tab Menu
6. Click Servo Gun Editor

#### SG_UserSRErrorToQuit
- KRC:\R1\TP\ServoGun\Userfiles
- Modify which Weld Errors are acknowledgeable via PLC inputs
  
#### Download Option Packages from KRC controller through Work Visual 5 and up (WoV 4 not compatible)
1. Open WorkVisual and connect to specific controller that option packages are on.
2. Switch to Programming and Diagnosis "workspace."
3. In "Cell Tree" (right window pane) CHECK the controller to have access to the controller settings and files.
4. In the top bar CLICK the orange monitor icon (Online System Information)
5. CHECK all required option packages in the window that appears from clicking the icon in step 4, and then CLICK "Download Selected."
6. Pick a directory to save the option packages and let them download.  Now they can be installed into the development instance of WorkVisual



#### Gun Compensation (Configures Robot to Move with Flexion of Gun Force)
- No Compensation = Dual Shank Configuration
- Air Compensation =  Electrode/Pedestal Configuration'
- Inline Form must be selected as "None" for compensation when using air compensation
- SG_TouchDiff[1]=0 - This function disables robot movement during the weld for pedestals
  

#### Burn-Off Determination
- Individual Measurement = Dual Shank Configuration
- Ratio in % = Electrode Configuration

#### Cell Tree Setup for Gun "Connection"
- Robot Mounted Gun = Connected to Robot in Cell Tree
- Pedestal Mounted Gun = Connected to Controller in Cell Tree

#### Gun Calibration Notes
- X-Compensation doesn't matter for gun calibration
- Maximum Threshold Factor = 2.5, Default Threshold Factor = 1.7

#### Correcting Robot Name after changing robot type
Using the variable monitor window, set
$robtrafo[] = $trafoname[]


---
		
## Motoman

Multi/Single Job -> Shift+4

Toggle Outputs -> Interlock+Select on Status Indicator/Dot

Copy/Paste Motions -> Shift+Select on MOVJ/L (then highlight selection)

Relative Job in utility tab in job

Soft Limits S*CxG 200-205 and 208-213  *Robot or EXT Axis

---
