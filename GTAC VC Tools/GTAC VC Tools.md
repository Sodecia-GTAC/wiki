# GTAC VC Tools

GTAC VC Tools is the shop app for laying out a cell, trimming the SSCC61x framework, drawing the EtherCAT trunk, and generating fixture and weld outputs.

Designed and built by Brandon, Dave, Mikey, and Richard, the guy that is never here.

Home has two sections. Robot holds the weld tools. PLC holds the TwinCAT tools. Project Board, GitHub, Wiki, and Local Server sit in the row underneath.

![Home with the Robot and PLC sections](./images/home-sections.png)

- [Home](#home)
- [Inside a tool](#inside-a-tool)
- [Robot](#robot)
  - [Weld Splitter](#weld-splitter)
  - [Weld Point Plotting](#weld-point-plotting)
  - [ArcTech Converter](#arctech-converter)
  - [Cycle Time Analysis](#cycle-time-analysis)
  - [Strip Arc to LIN](#strip-arc-to-lin)
  - [Zone Forge](#zone-forge)
- [PLC](#plc)
  - [Fixture Forge](#fixture-forge)
  - [TC Forge](#tc-forge)
  - [Controls Forge](#controls-forge)
- [Project Board](#project-board)
- [GitHub](#github)
- [Wiki](#wiki)
- [Local Server](#local-server)
- [Framework trim](#framework-trim)

## Home

- **Robot** (weld theme): Weld Splitter, Weld Point Plotting, ArcTech Converter, Cycle Time Analysis, Strip Arc to LIN, and Zone Forge. Click the Robot heading to open Weld Splitter.
- **PLC** (TwinCAT theme): Fixture Forge, TC Forge, and Controls Forge. Click the PLC heading to open Fixture Forge.
- **Bottom row**: Project Board, GitHub, Wiki, and Local Server.

Each tool name is a link, so it can open in a new tab. Guide at the top right says which tool fits the job. Click it again to close it.

![Home Guide](./images/home-guide.png)

There is no Weld Cell Forge start page anymore. Opening the weld app lands on Weld Splitter.

Old links still work. A bookmark such as ?app=weld, ?app=fixture, ?app=network, ?app=controls, ?app=zones, or ?app=board opens the same tool as before. ?app=weld without a screen, or with the old home screen, opens Weld Splitter.

## Inside a tool

Every tool has the same header. Home and the section drop-down are on the left. Change log, Clear saved work, GitHub, and Wiki are on the right.

The drop-down shows the section and the tool you are in, such as ROBOT, Weld Splitter. Hover over it, or click or tap it, to switch to another tool in that section. Go to PLC or Go to Robot at the bottom jumps to the other section. The keyboard works too: Enter or the down arrow opens it, the arrows move, and Escape closes it.

![Robot drop-down](./images/robot-menu.png)

![PLC drop-down](./images/plc-menu.png)

- **Guide**: Weld tools, Fixture Forge, TC Forge, and Controls Forge each have their own Guide. Click it again to close it.
- **Sample data**: The weld tools have Sample Project on the left. It loads the Front Bumper programs and that weld map. Click it again to clear it. Loading your own .src or zip turns the sample off. Fixture Forge has Load sample cell and Controls Forge has Load sample.
- **Change log**: Weld tools and Fixture Forge list what changed and when. It asks for the change-log password.
- **Saved work**: Work is saved in this browser only. It is still there after a refresh, but not on another PC or in another browser. Clear saved work resets that tool in this browser and cannot be undone.

## Robot

KUKA weld programs: split, plot, convert, time, and zone them. A weld program from GitHub (src, dat, zip, or pptx) opens in Weld Splitter.

The weld tools share the panel on the left (Sample Project, Guide, Program, and All robots) and one saved work. Weld Point Plotting does not use Program or All robots.

### Weld Splitter

![Weld Splitter with the sample program](./images/weld-splitter.png)

Group welds into modules and download the KUKA programs.

Drop the program .src and the positions .dat on Program. Both can go in at once. All robots takes one or more controller backup zips. If a zip has Sodecia/Weld_Jobs, only the programs in that folder are used.

My map is one module per line. Import map reads a weld-map PowerPoint or a JSON file you exported earlier. By part number skips the map and makes one module per weld family, plus All. Split job, then Download zip. Best cycle time keeps the order with the shortest travel between welds. Click Trunnion when the cell has a KP1 or KP3.

After you fix points in simulation, Upload Fixed Job from PRS takes the Process Simulate file that still has the UNKNOWN MOTION FOLD lines, plus its .dat. Fix PRS comment for Arc commands turns the commented arc lines back into ArcTech. Jobs Ready for Robot saves the corrected files.

### Weld Point Plotting

Plot the weld points onto the part each weld belongs to. Upload part CAD takes a STEP, IGES, STL, or OBJ. Upload weld XML places each weld on the part. Upload weld map is the PowerPoint that labels each dot. Click a name in the list to mark that weld. Drag to rotate.

### ArcTech Converter

Turn a Process Simulate download into ArcTech. Load one job, or Upload jobs for a zip or several .src files. UNKNOWN MOTION FOLD comes back as ArcOn, ArcSwi, and ArcOff. The .dat is not changed.

### Cycle Time Analysis

Seam and travel time from the weld map and the programs. Upload weld map and choose the PowerPoint. The seam time uses the millimetres on each weld label, such as 6041_96-25mm, divided by the weld speed. Load the program and the .dat on the left for a second table that adds travel between the points. Download analysis saves the tables as an Excel file. Blending and acceleration are not included, so a real cycle runs a bit longer.

### Strip Arc to LIN

Turn ArcOn, ArcOff, and ArcSwi into LIN moves. Load one .src and .dat, or Upload jobs zip for several. ArcOn and ArcOff become a fine LIN at 0.01 m/s. ArcSwi stays a LIN with C_DIS. A comment such as ; was ARCON WDAT1 marks each line so the arc can be taught again on the robot. The .dat files are not changed.

### Zone Forge

Fill in the interference-zone handshakes. Drop the KUKA programs and their .dat files, with the same name for both, such as R01_Fix01.src and R01_Fix01.dat. Process Simulate marks the last point before an interference volume and the first point after it.

Pick PLC bits or OLP sync. With PLC bits, assign one bit per pair of robots. 106 is the first pair, and robot interference uses 106 to 112. Bit 105 is the trunnion, or table, turn. Change a number to match the zone on the fixture, check What gets added, then Download the programs.

## PLC

TwinCAT fixtures, EtherCAT topology, and the cell's controls.

### Fixture Forge

![Fixture Forge](./images/fixture.jpg)

Open this when you have a fixture IO workbook. It writes the TwinCAT actions, the TcHMI screens, and the Process Simulate sequence from that sheet.

Drop the Excel map, or click Drop IO map and browse. Pick the fixture sheet. Copy the output into the matching POU or editor.

Workbook columns the generator reads:

- J / K — node (N01–N24) and port 0–7
- L / M — address (N01.I.0) and the description of use
- AC / AD — sequence of operation: step number and the action (Close, Open, Adv, Ret, grouped by model)

Sequence packs as part present, then clamps, pins, slides, and nut checks. Each new device type starts on port 0 of the next node. If a group ends on ports 0–6, the rest of that node is spare. Unused hardware is tagged Node Not Used.

On the TcHMI page, the layout can take the whole window. The left panel and the top band slide away. Click the arrow to bring them back. A screen you added can be deleted. The objects that were placed on it clear, so they can be placed again.

A fixture workbook from GitHub opens in this app.

### TC Forge

![TC Forge](./images/tc.jpg)

Open this when you already have the cable schedule, from Controls Forge or from a cell PDF. It draws the trunk, starting at IC01, and the cables that leave it.

Upload the cell PDF. The topology always starts at IC01. Download the drawing when you need a copy.

### Controls Forge

![Controls Forge](./images/controls.jpg)

Open this when you are laying out the cell. Cabinets, robots, options, and cables live here. Type a length and the cable part number shows up. The Package tab writes the keep list that trims the SSCC61x framework down to this cell.

#### Start a cell

Pick a project in the sample list and click Load sample. That fills the tabs from a real cell. Upload PDF does the same from a cable schedule: marks that end in -ECAT become the devices, the links, and the lengths. Clear puts the form back to empty.

If the PDF or the sample has no cell number on the end, the app asks for it before the serial is finished.

![Cell number](./images/cell-number.jpg)

#### Tabs

IPC holds the version, the safety gate, and where EtherCAT and Ethernet leave. Operator rows turn on the stack light, cycle start, and light curtains. Robots take the cabinet, the arm, the welder, and the reamer. Supply, nut welders, drops, stands, and fixtures are the rest of the chain. Connectors lists the plug on each cabinet. EtherCAT out is the next device.

#### Cables

![Cable list](./images/cables.jpg)

Cables lists every link the tabs describe. The connectors are already known from the devices. Type the length in meters and the part number comes from the lookup, including the maker and the connectors on the cable. No length yet means the cable is still waiting.

#### Topology PDF

![Cell 26013 EtherCAT topology](./images/topology-v4.jpg)
<!-- topology-drawing-v4 -->
PDF draws the EtherCAT trunk, starting at IC01, with the drops beside it. When the row hits the right side it continues on the left as another row. Download PDF puts that drawing on the first page and the cable list after it. TC Forge reads the marks that end in -ECAT.

A cell PDF from GitHub can open here or in TC Forge.

## Project Board

Which cell is late, and its GitHub repo. Red is late or has less time left than work left. Yellow is due within 14 days. Blue still has room.

The board starts with the built-in VC_Project_Board export. Drop export takes a newer CSV or Excel export. Drop OneNote updates the fixture reviews. Live refresh from Planner waits on IT. A GitHub name on a job opens that repository, once GitHub is connected in this browser.

## GitHub

GitHub is how a project gets into the app. The cell projects live in the organization https://github.com/Sodecia-GTAC-Machines.

There is no app login, name picker, or app 2FA code anymore. Your own GitHub token is the key, and GitHub decides what it can see.

![GitHub connect panel](./images/github-connect.png)

### Token

Make one of these on GitHub. Either kind works.

- **Classic token (simplest, one token for both)**: Settings, Developer settings, Personal access tokens, Tokens (classic). Generate a new token (classic).
  - Tick the repo scope only. Set an expiry of 30 days or less.
  - One classic token covers Sodecia-GTAC-Machines and the Sodecia-GTAC wiki.
  - It can reach every repo you can, so keep it short-lived.
  - If an organization uses SSO, click Configure SSO next to the token and authorize it for that organization.
  - If an organization blocks classic tokens, use a fine-grained token instead.
- **Fine-grained token**: Settings, Developer settings, Personal access tokens, Fine-grained tokens, Generate new token.
  - Resource owner Sodecia-GTAC-Machines, 30 days or less, only the repositories you need.
  - Contents read-only, or read and write only if you save files back.
  - Nothing else.

The value is shown once. A classic token starts with ghp_ and a fine-grained one with github_pat_.

### Connect

Click GitHub. Paste https://github.com/Sodecia-GTAC-Machines and the token, then Connect. The address has to be real text in the box, not the gray hint.

Wiki edit token is optional. Leave it empty and the token above is used for the wiki too. With a classic token, leave it empty. With fine-grained tokens, paste a second one there: resource owner Sodecia-GTAC, only the wiki repository, Contents read and write, 30 days or less. One fine-grained token cannot cover both organizations.

Tokens stay only in that browser tab. They are forgotten when the tab closes. Forget token clears them sooner.

If GitHub refuses the token, the panel says why. For SSO, authorize the token with Configure SSO. If the organization does not allow classic tokens, make a fine-grained one.

### Projects

The organization link lists the repositories. Search filters that list. Download on a repository saves the whole repo as a zip.

Open a repository, then a folder. Software is listed with Documentation, Hardware, and the rest. Download on a file saves that file, including files that do not open in an app.

- A workbook opens in Fixture Forge.
- A cell PDF opens in Controls Forge or TC Forge.
- A weld program opens in Weld Splitter.

## Wiki

Wiki opens this repository, Sodecia-GTAC/wiki, full screen. It starts on the README table of contents. Folders still lists the drawers. Search needs at least two letters and matches notes and headings. Reading needs no token.

Edit opens the markdown for the page you are on. Save commits it to main. New page asks for a path, such as Instructions/New note.md, then commits that file. Cancel throws the change away.

Saving uses the Wiki edit token, or the GitHub token when that field is empty. A classic token needs the repo scope. A fine-grained one needs Contents read and write on Sodecia-GTAC/wiki.

## Local Server

Run a copy on Ubuntu 24.04 Desktop or Windows 11. Local Server asks for its password, then shows the download, vc-tools-local.zip, and the install steps for each system. A publish does not change a Local Server that is already running. Download the zip again and follow When the app changes.

## Framework trim

![Framework package](./images/package.jpg)

The Package tab in Controls Forge writes the keep list. The scripts trim a copy of the SSCC61x framework down to that cell. Robot count can change from job to job. Do not hard-code a cell size.

### Serial

The serial is filled in on Package. SODG and two digits is the robot count. SSCC610 is the framework. The project number plus the cell number is the end. Four robots on 26013 cell 02 becomes SODG04_SSCC610_2601302.

### One folder for the trim kit

On the PC, make one folder and keep it outside the TwinCAT project. Documents\\PLC Trimming is fine. Download these five files from the Package tab into that same folder. The batch file only looks beside itself, so they have to stay together.

- Run-FwTrim.bat
- Pick-TrimPaths.ps1
- Prune-IoAndPlc.ps1
- Prune-SafetyXML.ps1
- CellKeep.ps1

Leave the framework where it already is. After the first run, last-trim.txt in the trim folder remembers both paths. When a script changes, replace the file in this folder. Do not keep an old copy next to the new one.

### Run it

1. Save the trim kit once, then double-click Run-FwTrim.bat.
2. Pick the keep list, then the folder that contains the .tsproj.
3. Leave one TwinCAT window open on that solution, with no dialogs. Two open projects are refused. If the open solution is a different serial than the keep list, the trim stops. An untouched framework is allowed through so it can be renamed.
4. The script renames the solution, the TwinCAT project, and the PLC project to the serial. A stray second solution file from the template name is removed.
5. The I/O prune removes EtherCAT devices that are not in the keep list. If the cell has no servos, it disables NC-Task 1 SAF and then removes that task. The rest of MOTION stays.
6. Close TcXaeShell when the batch file says to. The next script unlinks safety projects that are not in the keep list and deletes those folders. It writes GTAC_CONFIG and All_EstopRLYs_Off. It does not change .sal, .sds, or .diagram files.

### Finish safety by hand

Reload the solution, then:

1. In IC01.T02.EL6900, delete ST_Decouples only if this cell has no stud welder.
2. Delete IC_Decouple only if this cell has no extra controller. Otherwise leave it.
3. In Robot_Decouple, delete the red blocks for robots that are not in this cell.
4. Deactivate the unused inputs.
5. Run Verify Complete Safety Project.
