# GTAC wiki repo
This is the repository for the GTAC wiki.
Full of lots of informal notes created over the years, tips, tricks etc that may help you while working on a Sodecia GTAC machine


## Table of Contents

- [Auxiliary Equipment](./Instructions/Auxiliary%20Equipment%20Notes.md#auxiliary-equipment)
  * [GRACO](./Instructions/Auxiliary%20Equipment%20Notes.md#graco)
    + [Fluid Plate Setup (Lock Button to Access Setup Menus)](./Instructions/Auxiliary%20Equipment%20Notes.md#fluid-plate-setup--lock-button-to-access-setup-menus-)
      - [Controls Settings](./Instructions/Auxiliary%20Equipment%20Notes.md#controls-settings)
      - [Mode Settings](./Instructions/Auxiliary%20Equipment%20Notes.md#mode-settings)
      - [Delay Settings](./Instructions/Auxiliary%20Equipment%20Notes.md#delay-settings)
      - [Control Loop Settings](./Instructions/Auxiliary%20Equipment%20Notes.md#control-loop-settings)
      - [Pressure Sensors](./Instructions/Auxiliary%20Equipment%20Notes.md#pressure-sensors)
      - [Error Type](./Instructions/Auxiliary%20Equipment%20Notes.md#error-type)
      - [Maintenance Advisory Limits](./Instructions/Auxiliary%20Equipment%20Notes.md#maintenance-advisory-limits)
      - [Style](./Instructions/Auxiliary%20Equipment%20Notes.md#style)
      - [System Setup](./Instructions/Auxiliary%20Equipment%20Notes.md#system-setup)
  * [EMHART/STANLEY/TUCKER](./Instructions/Auxiliary%20Equipment%20Notes.md#emhart-stanley-tucker)
  * [NELSON](./Instructions/Auxiliary%20Equipment%20Notes.md#nelson)
      - [Fuses/Relays](./Instructions/Auxiliary%20Equipment%20Notes.md#fuses-relays)
  * [BRANSON](./Instructions/Auxiliary%20Equipment%20Notes.md#branson)
  * [Tox](./Instructions/Auxiliary%20Equipment%20Notes.md#tox)
  * [eWon VPN Setup](./Instructions/Auxiliary%20Equipment%20Notes.md#ewon-vpn-setup)
    + [Script Setup](./Instructions/Auxiliary%20Equipment%20Notes.md#script-setup)

---

- [Beckhoff](./Instructions/Beckhoff%20Notes.md#beckhoff)
    + [Important Side-notes](./Instructions/Beckhoff%20Notes.md#important-side-notes)
    + [XAE Compiler Check Boxes](./Instructions/Beckhoff%20Notes.md#XAE-compiler-checkboxes)
    + [ADSParseSymbol no more unused handles error](./Instructions/Beckhoff%20Notes.md#ADSParseSymbol-no-more-unused-handles-error)
    
  * [Addressing](./Instructions/Beckhoff%20Notes.md#addressing)
    + [ICxx Addressing](./Instructions/Beckhoff%20Notes.md#icxx-addressing)
    + [STxx Addressing](./Instructions/Beckhoff%20Notes.md#stxx-addressing)
    + [STxx Address Example](./Instructions/Beckhoff%20Notes.md#stxx-address-example)
    + [Rxx Addressing](./Instructions/Beckhoff%20Notes.md#rxx-addressing)
    + [Rxx Address Examples](./Instructions/Beckhoff%20Notes.md#rxx-address-examples)
    + [EP Block Address Settings](./Instructions/Beckhoff%20Notes.md#ep-block-address-settings)
    + [System Manager](./Instructions/Beckhoff%20Notes.md#system-manager)
      - [Setup AUTO Run Config/Verify Load Boot Project](./Instructions/Beckhoff%20Notes.md#setup-auto-run-config-verify-load-boot-project)
    + [SDxx Drive Notes:](./Instructions/Beckhoff%20Notes.md#sdxx-drive-notes-)
    + [System Manager Notes:](./Instructions/Beckhoff%20Notes.md#system-manager-notes-)
    + [Device State Errors](./Instructions/Beckhoff%20Notes.md#device-state-errors)
    + [Port Definitions](./Instructions/Beckhoff%20Notes.md#port-definitions)
    + [TwinSAFE](./Instructions/Beckhoff%20Notes.md#twinsafe)
      - [Normally Closed Inputs on FBs show inverted signal to actual input](./Instructions/Beckhoff%20Notes.md#normally-closed-inputs-on-fbs-show-inverted-signal-to-actual-input)
        * [SGs_COM_ERR - Connection Issue](./Instructions/Beckhoff%20Notes.md#sgs-com-err---connection-issue)
    + [Generating Master/Slave Messages from Rxx to IC01 6900 Connections](./Instructions/Beckhoff%20Notes.md#generating-master-slave-messages-from-rxx-to-ic01-6900-connections)
    + [FSoE Connection Info](./Instructions/Beckhoff%20Notes.md#fsoe-connection-info)
    + [TwinSAFE Notes:](./Instructions/Beckhoff%20Notes.md#twinsafe-notes-)
  * [PLC](./Instructions/Beckhoff%20Notes.md#plc)
    + [Setup GTAC Config](./Instructions/Beckhoff%20Notes.md#setup-gtac-config)
        * [Robot Setup](./Instructions/Beckhoff%20Notes.md#robot-setup)
        * [I/O Linking](./Instructions/Beckhoff%20Notes.md#i-o-linking)
        * [Fixture Setup](./Instructions/Beckhoff%20Notes.md#fixture-setup)
    + [Notes:](./Instructions/Beckhoff%20Notes.md#notes-)
    + [Logic Examples](./Instructions/Beckhoff%20Notes.md#logic-examples)

---

- [Indusoft Notes](./Instructions/Indusoft%20Notes.md#indusoft-notes)
    + [Indusoft/HMI Startup](./Instructions/Indusoft%20Notes.md#indusoft-hmi-startup)
    + [Generating Tag into Symbol File and Import Into Indusoft](./Instructions/Indusoft%20Notes.md#generating-tag-into-symbol-file-and-import-into-indusoft)
    + [Troubleshooting Notes](./Instructions/Indusoft%20Notes.md#troubleshooting-notes)
    + [Passing internal PLC variables out to IC](./Instructions/Indusoft%20Notes.md#passing-internal-plc-variables-out-to-ic)
    + [Modifying Symbol File for Each ICxx](./Instructions/Indusoft%20Notes.md#modifying-symbol-file-for-each-icxx)
    + [Copy Indusoft Screen Updates "Happily"](./Instructions/Indusoft%20Notes.md#copy-indusoft-screen-updates--happily-)
    + [Create Persistent Tags](./Instructions/Indusoft%20Notes.md#create-persistent-tags)
    + [Tag Driversheet Troubleshooting Tools](./Instructions/Indusoft%20Notes.md#tag-driversheet-troubleshooting-tools)

---

- [LVDT Notes](./Instructions/LVDT%20Notes.md#lvdt-notes)
    + [LVDT Setup (Zero'd & Offset from Calibrated Zero)](./Instructions/LVDT%20Notes.md#lvdt-setup--zero-d---offset-from-calibrated-zero-)
    + [LVDT Setup (Zero'd & Set from "No Load" Position)](./Instructions/LVDT%20Notes.md#lvdt-setup--zero-d---set-from--no-load--position-)
    + [LVDT Analog Output Range Adjustment](./Instructions/LVDT%20Notes.md#lvdt-analog-output-range-adjustment)

---

- [Robotic Notes](./Instructions/Robotic%20Notes.md#robotic-notes)
  * [KUKA](./Instructions/Robotic%20Notes.md#kuka)
      - [General Troubleshooting Tips](./Instructions/Robotic%20Notes.md#general-troubleshooting-tips)
      - [Kuka Relay Type](./Instructions/Robotic%20Notes.md#kuka-relay-type)
      - [Safety Monitoring Spaces on Human Zones](./Instructions/Robotic%20Notes.md#safety-monitoring-spaces-on-human-zones)
      - [Monitoring Space/Cell Perimeter Distances](./Instructions/Robotic%20Notes.md#monitoring-space-cell-perimeter-distances)
      - [Mastering Log](./Instructions/Robotic%20Notes.md#mastering-log)
      - [Axis Mastering Tips](./Instructions/Robotic%20Notes.md#axis-mastering-tips)
      - [Config Mon INI](./Instructions/Robotic%20Notes.md#config-mon-ini)
      - [Turn ON KRC AUX Relays (Safe OP)](./Instructions/Robotic%20Notes.md#turn-on-krc-aux-relays--safe-op-)
      - [VT_Direct() Setup/Info](./Instructions/Robotic%20Notes.md#vt-direct---setup-info)
      - [VT_Direct Example](./Instructions/Robotic%20Notes.md#vt-direct-example)
      - [Gun Approximation Direction (Servo_TC)](./Instructions/Robotic%20Notes.md#gun-approximation-direction--servo-tc-)
      - [Change Maximum Tip Wear](./Instructions/Robotic%20Notes.md#change-maximum-tip-wear)
      - [Fix Gun Tip Wear E1+ Limit Error](./Instructions/Robotic%20Notes.md#fix-gun-tip-wear-e1--limit-error)
      - [Increasing Weld Schedule Timeout](./Instructions/Robotic%20Notes.md#increasing-weld-schedule-timeout)
      - [Servo_TC Option Package/Servo Gun Editor in](./Instructions/Robotic%20Notes.md#servo-tc-option-package-servo-gun-editor-in)
      - [Decouple EXT Axis](./Instructions/Robotic%20Notes.md#decouple-ext-axis)
      - [Automatic Gun Calibration Tips](./Instructions/Robotic%20Notes.md#automatic-gun-calibration-tips)
      - [Adjust External Axis Home Position Tolerance](./Instructions/Robotic%20Notes.md#adjust-external-axis-home-position-tolerance)
      - [ASYNC_MODE Change](./Instructions/Robotic%20Notes.md#async-mode-change)
      - [ASYNC_AXIS Definition](./Instructions/Robotic%20Notes.md#async-axis-definition)
      - [Change Home Position Tolerance](./Instructions/Robotic%20Notes.md#change-home-position-tolerance)
      - [Ignore External Access for Master Reference](./Instructions/Robotic%20Notes.md#ignore-external-access-for-master-reference)
      - [Enable/Disable T2 Mode](./Instructions/Robotic%20Notes.md#enable-disable-t2-mode)
      - [Enable/Disable Brake Test (OLD FIX, no longer works correctly - 2021/10/07)](./Instructions/Robotic%20Notes.md#enable-disable-brake-test--old-fix--no-longer-works-correctly---2021-10-07-)
      - [Change $ROBROOT (Floor vs Ceiling Mounted Robot)](./Instructions/Robotic%20Notes.md#change--robroot--floor-vs-ceiling-mounted-robot-)
      - [Teach EXT TCP](./Instructions/Robotic%20Notes.md#teach-ext-tcp)
      - [Remove EXT gun from brake test](./Instructions/Robotic%20Notes.md#remove-ext-gun-from-brake-test)
      - [Example of Folds in KRL (Kinetic Rule Language)](./Instructions/Robotic%20Notes.md#example-of-folds-in-krl--kinetic-rule-language-)
      - [Example of Jumps in a Motion Program](./Instructions/Robotic%20Notes.md#example-of-jumps-in-a-motion-program)
      - [Gun Open Distance Setting](./Instructions/Robotic%20Notes.md#gun-open-distance-setting)
      - [Preparing Kuka WoV Package for Robot Commission](./Instructions/Robotic%20Notes.md#preparing-kuka-wov-package-for-robot-commission)
      - [ServoGun SG.INIT commands fail](./Instructions/Robotic%20Notes.md#ServoGun-SG-Init-commands-fail)
      
    + [Notes:](./Instructions/Robotic%20Notes.md#notes-)
    + [WTC/RAFT](./Instructions/Robotic%20Notes.md#wtc-raft)
      - [Increasing Weld Schedule Timeout](./Instructions/Robotic%20Notes.md#increasing-weld-schedule-timeout-1)
    + [WORK VISUAL](./Instructions/Robotic%20Notes.md#work-visual)
      - [External Axis Configuration Info](./Instructions/Robotic%20Notes.md#external-axis-configuration-info)
      - [Servo_TC Option Package/Servo Gun Editor in KUKA Work Visual Windows Application](./Instructions/Robotic%20Notes.md#servo-tc-option-package-servo-gun-editor-in-kuka-work-visual-windows-application)
      - [SG_UserSRErrorToQuit](./Instructions/Robotic%20Notes.md#sg-usersrerrortoquit)
      - [Download Option Packages from KRC controller through Work Visual 5 and up (WoV 4 not compatible)](./Instructions/Robotic%20Notes.md#download-option-packages-from-krc-controller-through-work-visual-5-and-up--wov-4-not-compatible-)
      - [Gun Compensation (Configures Robot to Move with Flexion of Gun Force)](./Instructions/Robotic%20Notes.md#gun-compensation--configures-robot-to-move-with-flexion-of-gun-force-)
      - [Burn-Off Determination](./Instructions/Robotic%20Notes.md#burn-off-determination)
      - [Cell Tree Setup for Gun "Connection"](./Instructions/Robotic%20Notes.md#cell-tree-setup-for-gun--connection-)
      - [Gun Calibration Notes](./Instructions/Robotic%20Notes.md#gun-calibration-notes)
      - [Correcting Robot Name after changing robot type](./Instructions/Robotic%20Notes.md#correcting-robot-name-after-changing-robot-type)
  * [Motoman](./Instructions/Robotic%20Notes.md#motoman)

---

- [Servo Notes](./Instructions/Servo%20Notes.md#servo-notes)
    - [Pulling Datasheet](./Instructions/Servo%20Notes.md#pulling-datasheet)
    - [Setting Parameters](./Instructions/Servo%20Notes.md#setting-parameters)
    - [Safety](./Instructions/Servo%20Notes.md#safety)
    - [Diagnosis](./Instructions/Servo%20Notes.md#diagnosis)

    ---

- [Vision Notes](./Instructions/Vision%20Notes.md#vision-notes)
  * [Kuka/VisionTech](./Instructions/Vision%20Notes.md#kuka-visiontech)
    + [Vision Task Setup Steps](./Instructions/Vision%20Notes.md#vision-task-setup-steps)
    + [Re-calibration](./Instructions/Vision%20Notes.md#re-calibration)
    + [Absolute Positioning](./Instructions/Vision%20Notes.md#absolute-positioning)
    + [Relative Positioning (Modelled Component)](./Instructions/Vision%20Notes.md#relative-positioning--modelled-component-)
    + [Notes:](./Instructions/Vision%20Notes.md#notes-)
      - [Pattern Training Settings](./Instructions/Vision%20Notes.md#pattern-training-settings)
      - [Run/Detection Parameters](./Instructions/Vision%20Notes.md#run-detection-parameters)
      - [Graphic Display Settings (Shown on image after task run)](./Instructions/Vision%20Notes.md#graphic-display-settings--shown-on-image-after-task-run-)
    + [License Handling (Work Visual & KRC Controller)](./Instructions/Vision%20Notes.md#license-handling--work-visual---krc-controller-)
    + [GigE Switch Configuration](./Instructions/Vision%20Notes.md#gige-switch-configuration)
    + [Troubleshooting](./Instructions/Vision%20Notes.md#troubleshooting)
  * [Cognex](./Instructions/Vision%20Notes.md#cognex)
    + [Calculation Example for FOV & Depth of Field](./Instructions/Vision%20Notes.md#calculation-example-for-fov---depth-of-field)
    + [Notes:](./Instructions/Vision%20Notes.md#notes--1)
  * [Keyence](./Instructions/Vision%20Notes.md#keyence)

  --- 

  - [Wiring & Cables Notes](./Instructions/Wiring&Cabling%20Notes.md#wiring---cables-notes)
      - [Note](./Instructions/Wiring&Cabling%20Notes.md#note)
    + [A Coded EtherNET 8 Wire (left to right)](./Instructions/Wiring&Cabling%20Notes.md#a-coded-ethernet-8-wire--left-to-right-)
    + [EtherCAT 4 Wire](./Instructions/Wiring&Cabling%20Notes.md#ethercat-4-wire)
    + [EtherCAT 4 Wire to RJ45 8 Pin](./Instructions/Wiring&Cabling%20Notes.md#ethercat-4-wire-to-rj45-8-pin)
    + [Transformer Thermal Connection (Green EtherCAT Wire on Robot)](./Instructions/Wiring&Cabling%20Notes.md#transformer-thermal-connection--green-ethercat-wire-on-robot-)
    + [Beckhoff Fieldbus Power 4 Wire](./Instructions/Wiring&Cabling%20Notes.md#beckhoff-fieldbus-power-4-wire)
    + [SMC Fieldbus Power 4 Wire](./Instructions/Wiring&Cabling%20Notes.md#smc-fieldbus-power-4-wire)
    + [SMC Fieldbus Power 5 Wire (7/8" Connection)](./Instructions/Wiring&Cabling%20Notes.md#smc-fieldbus-power-5-wire--7-8--connection-)
    + [EP9224 Brad Harrison Power](./Instructions/Wiring&Cabling%20Notes.md#ep9224-brad-harrison-power)
    + [CBL-INT-PS1 to EP9224](./Instructions/Wiring&Cabling%20Notes.md#cbl-int-ps1-to-ep9224)
      - [SMC Pressure Switch Analog Signal 4 Wire (into 3174)](./Instructions/Wiring&Cabling%20Notes.md#smc-pressure-switch-analog-signal-4-wire--into-3174-)
    + [Load Cell (Seat Belt)](./Instructions/Wiring&Cabling%20Notes.md#load-cell--seat-belt-)
    + [Teach Mode Beacon Light (OP2-SL1)](./Instructions/Wiring&Cabling%20Notes.md#teach-mode-beacon-light--op2-sl1-)
    + [Keyence GT2 LVDT 4 Wire](./Instructions/Wiring&Cabling%20Notes.md#keyence-gt2-lvdt-4-wire)
    + [Euchner Gate Wiring](./Instructions/Wiring&Cabling%20Notes.md#euchner-gate-wiring)
    + [SIC Marker Start Stop Pod](./Instructions/Wiring&Cabling%20Notes.md#sic-marker-start-stop-pod)
    + [Thermal Wiring (Inside Transformer)](./Instructions/Wiring&Cabling%20Notes.md#thermal-wiring--inside-transformer-)
    + [M8 Fieldbus Power 4 Wire](./Instructions/Wiring&Cabling%20Notes.md#m8-fieldbus-power-4-wire)
    + [Beckhoff ZK2030 Power Cable Pinout](./Instructions/Wiring&Cabling%20Notes.md#beckhoff-zk2030-power-cable-pinout)
    + [IFM Camera Power & I/O 8 Wire](./Instructions/Wiring&Cabling%20Notes.md#ifm-camera-power---i-o-8-wire)
      - [Output Node (S1)](./Instructions/Wiring&Cabling%20Notes.md#output-node--s1-)
      - [Input Node (S2)](./Instructions/Wiring&Cabling%20Notes.md#input-node--s2-)
    + [Cognex Camera Power & IO 12 Wire](./Instructions/Wiring&Cabling%20Notes.md#cognex-camera-power---io-12-wire)
      - [Input Node (S1)](./Instructions/Wiring&Cabling%20Notes.md#input-node--s1-)
      - [Output Node (S2)](./Instructions/Wiring&Cabling%20Notes.md#output-node--s2-)
    + [ifm Standard 8 Pin Connector](./Instructions/Wiring&Cabling%20Notes.md#ifm-standard-8-pin-connector)
    + [Cognex Standard 12 Pin Wire Colour](./Instructions/Wiring&Cabling%20Notes.md#cognex-standard-12-pin-wire-colour)
    + [Murr Standard 12 Pin Wire Colour](./Instructions/Wiring&Cabling%20Notes.md#murr-standard-12-pin-wire-colour)
    + [Leuze 8 Pin Standard Wire Colour](./Instructions/Wiring&Cabling%20Notes.md#leuze-8-pin-standard-wire-colour)
    + [Phoenix Contact 8 Pin Standard Wire Colour](./Instructions/Wiring&Cabling%20Notes.md#phoenix-contact-8-pin-standard-wire-colour)
    + [Phoenix Contact 5 Pin Standard Wire Colour](./Instructions/Wiring&Cabling%20Notes.md#phoenix-contact-5-pin-standard-wire-colour)
    + [Kuka KR6/10 X41 Wiring (Gripper M12 8pin plug)](./Instructions/Wiring&Cabling%20Notes.d#kuka-kr6-10-x41-wiring--gripper-m12-8pin-plug-)
    + [Water Stands (Non-IO Link)](./Instructions/Wiring&Cabling%20Notes.md#water-stands--non-io-link-)
      - [Water Stand Turck Connections into 3174](./Instructions/Wiring&Cabling%20Notes.md#water-stand-turck-connections-into-3174)
      - [From Solenoid End Connection to 2028](./Instructions/Wiring&Cabling%20Notes.md#from-solenoid-end-connection-to-2028)
      - [Water Stands (IO-Link)](./Instructions/Wiring&Cabling%20Notes.md#water-stands--io-link-)
    + [Profibus Connector to 4Pin Pass-through](./Instructions/Wiring&Cabling%20Notes.md#profibus-connector-to-4pin-pass-through)
    + [Graco CAN/DeviceNET Connector 5Pin](./Instructions/Wiring&Cabling%20Notes.md#graco-can-devicenet-connector-5pin)
    + [Sic laser DB37 wiring](./Instructions/Wiring&Cabling%20Notes.md#sic-laser-db37-wiring)
    + [3 Phase into KUKA](./Instructions/Wiring&Cabling%20Notes.md#3-phase-into-kuka)
    + [PD Shut Off Bar Length](./Instructions/Wiring&Cabling%20Notes.md#pd-shut-off-bar-length)
    + [Cable Package Amounts](./Instructions/Wiring&Cabling%20Notes.md#cable-package-amounts)
      - [ICxx](./Instructions/Wiring&Cabling%20Notes.md#icxx)
      - [Fixture](./Instructions/Wiring&Cabling%20Notes.md#fixture)
      - [Stack Light, Cycle Starts, & Safety Gate](./Instructions/Wiring&Cabling%20Notes.md#stack-light--cycle-starts----safety-gate)
      - [Light Curtains](./Instructions/Wiring&Cabling%20Notes.md#light-curtains)

---

- [GIT](./Instructions/Git.md)
    + [Installing](./Instructions/Git.md#Installing)
    + [Common Terms](./Instructions/Git.md#Common-Terms)
    + [Using](./Instructions/Git.md#Using)
    + [Practice](./Instructions/Git.md#Practice)

---

## Internal Github GTAC Links
  - [Informal Q&A Sessions with Brent](https://github.com/orgs/Sodecia-GTAC/discussions/5)
    

    
## External Links
  - [Beckhoff Error Codes Link](https://infosys.beckhoff.com/english.php?content=../content/1033/devicemanager/263043211.html&id=)





## Travel Checklist

- [Controls Travel Checklist](./Instructions/Travel%20Checklist.md#controls-travel-checklist)
    + [Documents](./Instructions/Travel%20Checklist.md#documents)
    + [Tools](./Instructions/Travel%20Checklist.md#tools)
    + [PPE](./Instructions/Travel%20Checklist.md#ppe)
    + [Electronics](./Instructions/Travel%20Checklist.md#electronics)
    + [Other Recommended Personal Items](./Instructions/Travel%20Checklist.md#other-recommended-personal-items)
  * [Travel Tips](./Instructions/Travel%20Checklist.md#travel-tips)
    + [Personal Items you may want but may not be necessary for everyone](./Instructions/Travel%20Checklist.md#personal-items-you-may-want-but-may-not-be-necessary-for-everyone)


