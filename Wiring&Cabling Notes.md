Our I/O = PNP(Sourcing) NOT NPN(Sinking)


A Coded EtherNET 8 Wire (left to right)

1 - Green/White (Pair 1-2)
2 - Green (Pair 1-2)
3 - Orange/White (Pair 3-4)
4 - Blue (Pair 3-4)
5 - Blue/White (Pair 5-6)
6 - Orange (Pair 5-6)
7 - Brown/White (Pair 7-8)
8 - Brown (Pair 7-8)

EtherCAT 4 Wire

1 - Yellow OR White/Orange
2 - White OR White/Blue
3 - Blue
4 - Orange

EtherCAT 4 Wire to RJ45 8 Pin

1 - Yellow
2 - Orange
3 - White
4 - Blank
5 - Blank
6 - Blue
7 - Blank
8 - Blank

Transformer Thermal Connection (Green EtherCAT Wire on Robot)

1 - Orange
2 - White
3 - Yellow
4 - Blue

Beckhoff Fieldbus Power 4 Wire

1 - Brown 24V+ Us (Supply)
2 - White 24V+ Up (Output)
3 - Blue 0V
4 - Black 0V

SMC Fieldbus Power 4 Wire

1 - White
2 - Black
3 - Brown
4 - Blue

SMC Fieldbus Power 5 Wire (7/8" Connection)

[add picture here]


EP9224 Brad Harrison Power

1 - Wire 1 (0V) 
2 - Wire 2 (0V)
3 - Ground
4 - Wire 4 (24V)
5 - Wire 3 (24V Switched)

CBL-INT-PS1 to EP9224

1 - Wire 1 (0V)
2 - Wire 2 (0V)
3 - Blank
4 - Wire 3 (24V)
5 - Wire 4 (24V Switched) 
6 - Blank

SMC Pressure Switch Analog Signal 4 Wire (into 3174)

1 - Brown 24V+
2 - White [Signal+ 4-20mA]
3 - Blue 0V
4 - Jumper from 3 [Signal- (Reference)]
*Black Wire can be cut, as it is not used

Load Cell (Seat Belt)

1 - Red
2 - White
3 - Black
4 - Green

Teach Mode Beacon Light (OP2-SL1)

1 - BLANK
2 - Red Wire
3 - Black Wire
4 - BLANK

Keyence GT2 LVDT 4 Wire
1 - Brown
2 - Orange 
3 - Blue
4 - Green
*Cut other 8 wires (Only Analog Signal utilized)

Euchner Gate Wiring
1 - White (24v Supply) [Terminal 11+33]
2 - Brown (CH1.1) [Terminal 21]
3 - Green (0v Common) [LED Commons]
4 - Yellow (CH2.1) [Terminal 41]
5 - Grey (CH1.2) [Terminal 22]
6 - Pink (CH2.2) [Terminal 42]
7 - Blue (0v Relay) [Terminal E2]
8 - Red (24v Relay) [Terminal E1]
*Wire 9-12 Not Used

SIC Marker Start Stop Pod

Stop = Brown/White
Start = Green/Yellow

Thermal Wiring (Inside Transformer)
- Brown/White Wires from Transformer
- Black/White Wires from 4 pin passthrough

M8 Fieldbus Power 4 Wire

[add picture here]

[add picture here]


Beckhoff ZK2030 Power Cable Pinout

1 - Black
2 - Blue
3 - Grey
4 - Brown
5 - White
[add picture here]


IFM Camera Power & I/O 8 Wire

Output Node (S1)
1 - Pin1 - U+
2 - Pin2 - Trigger Input
3 - Pin3 - 0V
4 - Pin4 - Switching Output/Trigger Output
Input Node (S2)
1 - N/A - Switching Output (Ready)
2 - Pin6 - Switching Output (OUT)
3 - N/A - Switching Output/Input
4 - Pin8 - Switching Output/Input

*Wire7+8 can be cut at the 8 pin connection into the Y split to have Pin5+7 disconnected

Cognex Camera Power & IO 12 Wire

Input Node (S1)
1 - Red (24VDC)
2 - Grey (Input 2)
3 - Black (0VDC)
4 - Blue (Input 1)
Output Node (S2)
5 - Green (Output Common) 
6 - Violet (Output 2)
7 - White/Violet (Input Common) 
8 - Orange (Trigger)
UNUSED
9 - Yellow (IN 3)
10 - White/Yellow (IN 4)
11 - Brown (OUT 3)
12 - White/Brown (OUT 4)

ifm Standard 8 Pin Connector

1 - Brown
2 - White
3 - Blue
4 - Black
5 - Grey
6 - Pink
7 - Violet
8 - Orange (Middle)

Cognex Standard 12 Pin Wire Colour

1 - Yellow
2 - White/Yellow
3 - Brown
4 - White/Brown
5 - Violet
6 - White/Violet
7 - Red
8 - Black
9 - Green
10 - Orange
11 - Blue
12 - Grey

Murr Standard 12 Pin Wire Colour

1 - Brown
2 - Blue
3 - White
4 - Green
5 - Pink
6 - Yellow
7 - Black
8 - Grey
9 - Red
10 - Violet
11 - Grey/Pink
12 - Red/Blue

Leuze 8 Pin Standard Wire Colour


1 - White
2 - Brown
3 - Green
4 - Yellow
5 - Grey
6 - Pink
7 - Blue
8 - Red


Phoenix Contact 8 Pin Standard Wire Colour

1 - Brown
2 - White
3 - Black
4 - Pink
5 - Grey
6 - Yellow
7 - Green
8 - Red

OR

1 - White
2 - Brown
3 - Green
4 - Yellow
5 - Grey
6 - Pink
7 - Blue
8 - Red



[add picture here]


Phoenix Contact 5 Pin Standard Wire Colour

1 - Brown
2 - White
3 - Blue
4 - Black
5 - Grey

Kuka KR6/10 X41 Wiring (Gripper M12 8pin plug)
[add picture here]


---
Water Stands (Non-IO Link)
Water Stand Turck Connections into 3174

1 - Wire 2 Top/Outside Flow Meter
2 - Wire 1 Top/Outside Flow Meter
3 - Wire 2 Bottom/Inside Flow Meter
4 - Wire 1 Bottom/Inside Flow Meter

Wire 2 = one with white label/sticker

From Solenoid End Connection to 2028
Wire 1 - - - Pin 1 - Pin 4 (Positive Switch)
Wire 2 - - - Pin 2 - Pin 3 (Negative)

Water Stands (IO-Link) 

Port 1 - M12 5 Pin from Flow Switch 1
Port 2 - M12 5 Pin from Flow Switch 2
Port 3 - Valve Plug/M12 5 Pin from Water Solenoid
Port 4 - Blank

---
Profibus Connector to 4Pin Pass-through
---------  - +24V Pin 1
Green  - A to Pin 2
---------  - 0V Pin 3
Red     - B to Pin 4

!!! EL6731 (MASTER) CONNECTION WIRES INTO IN CONNECTION!!!
Strip 55mm for wiring in ZB3100, 3mm of shielding

[add picture here]


Graco CAN/DeviceNET Connector 5Pin
1 - Bare (Shield) 
2 - Red (+ Voltage) 
3 - Black (- Voltage) 
4 - White (Can_H) 
5 - Blue (Can_L)

Sic laser DB37 wiring
3  -  Brown (From PD) 
4  -  Blue (From PD) 
5  -  White (From PD) 
6  -  Black (From PD) 
7  -  Brown (From safety switch)
8  -  Blue (From safety switch)
9  -  Violet (From safety switch)
10 -  Violet white (From safety switch)

3 Phase into KUKA

1 - Red
3 - Black
5 - Blue

Hydraulic Knockout Bit = V Size

PD Shut Off Bar Length
- Small Bar = 190mm
- Large Bar = 180mm
---
Cable Package Amounts

ICxx
	 [] PD to ICxx Power Cable (20-150ft)
	 [] Ethernet to ICxx (~50ft)
	Fixture
	 []  2x 10m 8mm 4 Pin Power Cable
	 []  2x 10m 8mm-12mm 4 Pin EtherCAT
	Stack Light, Cycle Starts, & Safety Gate
	 []  2x 5m 5 Pin I/O Cable (SLxx)
	 []  2x 0.6m 8 Pin I/O Cable (CSxx)
	 []  1x 10m 8 Pin I/O Cable (SGxx)
	 []  1x 5m 8 Pin I/O Cable (Ext Option)
	Light Curtains
	 []  2x 5m 5 Pin I/O Cable
	 []  2x 5m 8 Pin I/O Cable
	 []  2x 10m 5 Pin I/O Cable
	 []  2x 10m 8 Pin I/O Cable
	






