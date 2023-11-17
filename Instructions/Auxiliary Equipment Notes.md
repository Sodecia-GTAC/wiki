# Auxiliary Equipment

## GRACO

### Fluid Plate Setup (Lock Button to Access Setup Menus)

#### Controls Settings
- Dispense Trigger Source: Gateway
- Enable Valves: 1 - OFF, 2 - OFF, 3 - OFF, 4 - OFF
- Command Value Source: Display
- Job End Mode: Gateway
- Job End Delay: [only available with Job End Mode = Timer]
- Run Mode Bead Adjust: Enable
- End Job On Alarm: OFF
- Display Control Password: Disable

#### Mode Settings
- Mode = Full Open
- Bead Scale = 100%

#### Delay Settings
- Valves
	- On (ms): 0
	- Off (ms): 0
- Regulator
	- On (ms): 0
	- Off (ms): 0

#### Control Loop Settings
- Pressure
	- Kp: 32
	- Ki: 128
	- Kd: 0
- Bead
	- Kp: 32
	- Ki: 128
- Meter Type: Volume
- K-Factor: 33000 pulses/Litre

#### Pressure Sensors
- Inlet Offset: (Offset until no pressure reads 0)
- Outlet Offset: (Offset until no pressure reads 0)
- Min Inlet: 2000 psi
	- Error Type: Alarm
- Max Inlet: 5000 psi
	- Error Type: Alarm
- Max Outlet: 5000 psi
	- Error Type: Alarm

#### Error Type
- Low Pressure: Deviation
- High Pressure: Deviation
- Low Flow Rate: Deviation
- High Flow Rate: Deviation
- Low Material: Alarm
- High Material: Deviation
- Low Computed Target: Alarm
- High Computed Target: Deviation

#### Maintenance Advisory Limits
- Supply: 0
- V/P: 0
- Regulator: 0
- Flowmeter: 0
- Valves: 0

#### Style
- Style Name: (Application Specific)
- Volume: (Application Specific)
- Tolerances: -5% / +10%
- Pre Charge
	- Mode: Display
	- Pressure: 1000 psi
- Swirl Association (ONLY used with Swirl Head)
- Valves: None
- Motor Fault: Deviation

#### System Setup
- Enable Quantity of dispensing heads and swirl orbiters here
Gateway Setup
- Set Profibus Address here.  Device Address
Advanced Setup
- Setup Date/Time, Measurement Units, Backup Settings, and Verify/Update Software Version

---
## EMHART/STANLEY/TUCKER

- Verify all ferrous materials are at least 2 inches away from any drawn arc weld (prevents magnetism build up)

---
## NELSON

Step 3 after stud touch.
 
Checked over 40ms period during pilot (touching part)
- NO ARC = during pilot low voltage, possibly short.
- ARC LOSS = high voltage, ARC occurred but was lost.
Step 4 lifting from part, to achieve current
2ms check of current rise, if it doesn't reach 200amp it will come up with fault.  CURRENT LEVEL
 
Step 5 plunging to part after current is met (as the current is starting to lower)
 
Wait for cool.  About 100ms
 
NIO WELD didn't meet all weld specs over weld process.
- Voltage should mirror gun movement
- Voltage drop usually is the result of arcing
 
IF NIO Welds are consistent try the following:
- Increasing dwell time before weld to get stable contact to the part
- Increase lift distance to build a bigger arc and generate more heat
- Increasing the robot distance away from gun to allow stud gun to stroke more and give more distance for lift
- Increase Plunge Time/Plunge Depth to seat into the molten pool more (won't work if not building enough of an ARC)
- LAST OPTION - open parameters to allow more tolerance on welds - !!!NOT A GOOD OPTION!!!

Notes:
- Gun SYNC ETV delays or advances the plunge time after the lift/drawn arc

---
Stud ARC goes toward MASS and away from GROUND.
 
1.  Current is stepped down then rectified.
 
2. Stored in capacitor.
 
3. Load resistor takes current during pilot.
 
4.  Weld module regulates the current out of the capacitor.  DC across the main coil and shunt.  Closed loop system.
- MOSFET controls weld modules from KAS-INTER board
- Voltage and current feedback into KAS-INTER board
- AUSGTHY board determines gun that gets current SCR controlled.  This is
where it confirms contact
 
#### Fuses/Relays
 
F11 should always be OFF, the rest should be always ON.
K1 is main relay
K2 is emergency relay

---
## BRANSON

Plastic weld joint is created at the first point of contact for the mated plastic components (There should not be fusion in other areas besides this)


Welding by Time OR Energy are the best methods

- Pre-Trigger =  Starts the frequency before Trigger Pressure is achieved
- smaller horns can develop their frequency easier and do not need a pre-trigger, but larger horns may need this
- Trigger Pressure = ONLY required when pressing the components together
- IF the components can mate together without much tension then LOW trigger pressure should be used
- Each notch on the trigger pressure dial is equivalent to 10 pounds of force (EG. 12 = 120 pounds)
- Energy = "Work Over Time"  (Peak Power x Time -- roughly)
- Amplitude = the Intensity/Aggression/Force of the frequency  (Height of the frequency wave)
- Afterburst = Applies a frequency to the horn as it retracts AFTER WELDING
- Helps release welded components and prevents them from sticking to the horn on its upstroke
- Peak Power = power supply's duty cycle during the weld cycle (NOT a control parameter)
- Dead Stop = mechanical stop to prevent welding IF stroke exceeds expected position (Prevents crashing the horn)
- Set on the side of the Branson Unit

---

## Tox

Notes:
- To Enable Window Measurement Output on PRofiBUS, must enable Final Values -- Menu > Supplement > Communication Parameters > Profibus Address >[check log final values on profibus]


---
## eWon VPN Setup


Setup Steps
1. Install E-Buddy and Set IP of eWON to 172.16.1.53
2. Login with default user/password = adm/adm
3. Use the 3 wizards to setup the Ewon system:
	1. System for changing the Ewon name to machine name AND user to GTAC/password to ************** (consult GTAC Engineering) 
	2. Internet is setup as DHCP and verify internet connection
	3. VPN sets up the Talk2M connection with eCatcher software.  The code is generated in eCatcher OR enter eCatcher account name and credentials.  (Use TCP for connection under Advanced Parameters If UDP fails)


VPN Toggle ON/OFF (Tag Setup)

Enable Setup Mode on Tag screen and Click Edit, which opens Tag Configuration Screen

Setup Tag Parameters the same as below, leave other settings default

Return Tag Mode to View after completing tag setup


### Script Setup

Add below script line to INIT Section

ONCHANGE "Switch", "Goto DoSwitch"

Then click the + button to add "Enable_WAN" Section, then copy below script and paste into the new section

REM --- eWON user (start)
DoSwitch:
IF (Switch@<>0) THEN
REM Open Internet connection
SETSYS COM,"load"
REM --- WANCnx = 2 for Ethernet
SETSYS COM,"WANCnx","2"
SETSYS COM,"WANPermCnx","1"
SETSYS COM,"save"
PRINT Time$;" Connection opened"
ELSE
REM Close Internet connection
SETSYS COM,"load"
REM --- WANCnx = 0 for Disabled
SETSYS COM,"WANCnx","0"
SETSYS COM,"save"
PRINT Time$;" Connection closed"
ENDIF
END


Finally under the run tab select "Autorun" and then change the script to run in the top right corner.  This will prompt it to be saved.  Save the script and it should now be running.

---






