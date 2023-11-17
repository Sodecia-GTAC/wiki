Pulling Datasheet: to pull the Drive datasheet go to -> Drive in IO Tree > Drive Manager tab > Channel (A or B) > Configuration > Motor and Feedback > Motor > Datasheet, then select X1424 then click "Read Datasheet from EPROM"

Setting Parameters

In Drive Manager > Scaling and NC Parameters - there is a button labeled "Set NC Parameters," and this must be clicked before downloading to the drive as the parameters will not update without this step

Linking the Axis in the NC configuration will automatically link all required connections

---
NC - Configuration > Axes > [specific axis # here] > [specific axis # here]_Enc

This directory leads to the Parameters tab to offset the servo position (position bias)

---
Click [configured instance of servo in SysMan] > click Motor & Feedback > click "Scan feedback 1/Motor" 

This directs to the location to scan in new Servo Drives

---
Safety

"Number of Axes" is not determined by number of connected motors, but simply how many motors the drive is configured to handle (second digit of the AX part number) 
- [5805 Alias Device > Safety Parameter Tab > Index 2F00] (TwinCAT 3)

For any motor that is not connected to the AX drive, STO Mode must be set TRUE 
- Motor 1 [5805 Alias Device > Safety Parameter Tab > Index 2041] (TwinCAT 3)
- Motor 2 [5805 Alias Device > Safety Parameter Tab > Index 2841] (TwinCAT 3)

You need to manually set "Motor_Polepairs"
- [5805 Alias Device > Safety Parameter Tab > Index 2001] (TwinCAT 3)
- [5805 Alias Device > Safety Parameter Tab > Index 2802] (TwinCAT 3)

You need to manually set "Motor_String"
- [5805 Alias Device > General] (TwinCAT 3)

To Enable FSoE on a new drive go to the AX5805 > Safe Parameter -- Then manually enter the drive string into the specific Motor String field (this value can be found in Drive Manager in the "Order Code:" field) 

To get the FSoE Master and Slave Messages

Create instance uses of the specific AX5805 in TwinSAFE Function Blocks and the Connection will automatically be created in the Connection list

Changing AX5805 parameters requires downloading the associated EL6900 safety code (Usually PD)

---
Diagnosis

Port A = X04 EtherCAT connection port
Port B = X05 EtherCAT connection port
Port D = AX5805 connection port

AL Status 0x0045 - "MBX SoE'  = Mailbox Servo over EtherCAT - this relates to parameters not being set correctly

To find parameter error within a configured drive go to [specific drive] in SysMan tree >SoE Online > S-0-0021 and S-0-0022 then double click this to see a list of parameters causing errors.  These will lead to Drive Manager > Parameter List

"Axis/Group or coupled slave axis has none enabled controller and, therefore, does not take an instruction (error-code 0x4260)"
- This message refers to the fact that the enable conditions (from the PLC) are not allowing the Axis to move. 
