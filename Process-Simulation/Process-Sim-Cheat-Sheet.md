🔧 Simulation ↔ PLC/UI OPC Connection Cheat Sheet (TwinCAT / TMC)
📌 Common Issue

Simulation (SIM Study), PLC, or UI won’t connect or behave correctly via OPC.

⚠️ Root Cause (Typical)

Mismatch between:

Simulation I/O interface (standard FW vs workaround/custom)
PLC project
TMC file used by OPC server

👉 Especially common in newer projects like Bumpers cell, where I/O structure has evolved.

✅ Quick Checks (Do This First)
Verify correct TMC file is loaded in OPC server
Confirm simulation is using the expected I/O interface
Check if project uses:
Standard FW interface
OR custom/workaround interface
Restart OPC server after any TMC update

🧪 Symptoms You’ll See
OPC tags missing or not updating
UI not responding to simulation
PLC logic running but no feedback in SIM
Random or incorrect signal mapping

🛠️ Fix / Workaround
Replace OPC server TMC file with latest from PLC project
Confirm TMC matches:
Current simulation version
Current I/O structure
Restart OPC server / reconnect clients
Re-test SIM Study

🧠 Lesson Learned

If the simulation interface changes, the TMC must be updated—or OPC will silently break.

---

<p align="center">
  <img src="./assets/vc-logo.png" width="120"><br>
  <sub>VC Team | Simulate. Integrate. Innovate.</sub>
</p>