LVDT Setup (Zero'd & Offset from Calibrated Zero)
1. Get LVDT in measurement position of the “zero” using a measured work piece designated as such.
2. Once in the “zero” measuring position - on the LVDT unit press the PRESET button to zero the LVDT to the current measuring position.  
3. Now release the LVDT to it’s "no load" state (If the value on the LVDT is negative you must offset it from the LVDT unit to get it reading 0 and upwards)
4. To offset the LVDT, you must use the left and right arrow buttons to find the PRESET setting on the display, once there use the UP and DOWN buttons to offset the PRESET until the "no load" condition measures zero.  (negative values will not register through the raw data on the analog input node)
5. Once the "no load" position measurement reads 0 you can offset the LVDT value used in the PLC which is usually HMI controlled.  (The Offset control is located on the HMI screen where the associated LVDT is viewed)
6. Bring the tool into the measurement position with the “zero” work piece, and the now LVDT values will display and measure their value equal to the ones on the LVDT.
7. Then login to the PLC and verify the scaled values in each LVDT instance to match the minimum and maximum LVDT displayed values.

LVDT Setup (Zero'd & Set from "No Load" Position)
1. Get LVDT in a "no load" condition where the probes are not measuring anything in their "free" state.
2. Once in the "no load" state - on the LVDT unit press the PRESET button to zero the LVDT to the current position. 
3. Verify the scale from the LVDT to the PLC by logging into the PLC and checking the scaled values in each LVDT instance are matching the minimum and maximum LVDT displayed values.

LVDT Analog Output Range Adjustment

The Output Range can be changed to alleviate fluctuation issues with measuring equipment.  Tightening the Output Range can increase the sensitivity and move the measurement fluctuation further down the decimal points to remove the fluctuation from the captured measurement.

1. Open settings by holding "MODE" and "SET" for 2 seconds.
2. Once in the settings menu, go to item 16 "AnG."
3. Change this item from "dEFALt" to "FrEE."  (This will unlock the analog output range)
4. Now set item 17 and 18 Analog High and Analog Low which were unclocked by changing Item 16.

---
