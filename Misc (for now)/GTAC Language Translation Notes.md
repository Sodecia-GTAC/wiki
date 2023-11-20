 


# GTAC Language Translation File guide

## Document Purpose
This document is to be used as a guide to help you navigate generating a new GTAC_Translation_File should translation need to be added / edited. 


This is by no means an exhaustive document on the subject…….

![Mapper Example](./GTAC%20Language%20Translation%20Images/Mapper%20Example.png)


In the following example we sent out all our standard fault text and asked that it be translated to Czech so that this could be added to our machine’s language translations. We now need to get this new Czech text into our GTAC_Language_Translation file for use on our UI package.

 

We will be working with three files:
- Translated text working file:
    -	this is the file that we sent with a list of text to be translated and was returned to us with translated texts Master Translation 
- Mapper_yyyymmddinitials:
  - This is the master record of all our latest GTAC translations
  - The end of file name is out standard yyyymmdd and initials to indicate the last edit date and editor
- GTAC_Translation_File:
  - This is the end translation file that we place into our IWS UI package folder. It is what IWS uses when we select a different language for our UI displays

---

### Step 1:
Open the translated text working file provided by the technical documentation department and confirm the text you asked to be translated has been completed. If the text being translated was fault code text, be sure the Fault Number formula was preserved.
![Step 1](./GTAC%20Language%20Translation%20Images/Step%201.png)


### Step 2:
Rename the Master Translation Mapper file to the current date and add your initials
 ![Step 2](./GTAC%20Language%20Translation%20Images/Step%202.png)


### Step 3:
Open the Master Translation Mapper file in MS Excel, update the “Last Edited:” cell under English
 ![Step 3](./GTAC%20Language%20Translation%20Images/Step%203.png)

### Step 4:
Back to the translation working file, select the cells that contain the translated text, right click and copy
 ![Step 4](./GTAC%20Language%20Translation%20Images/Step%204.png)

### Step 5: 
Back to the master Translation Mapper, scroll to the appropriate language column for the translated text you will be adding and then scroll down to the appropriate are the text is to be place in, right click and paste. Note: if you are pasting fault text, you may need to select a different paste option then shown to preserve the formulas.
![Step 5](./GTAC%20Language%20Translation%20Images/Step%205.png)
 

### Step 6:
 Once you have added in all the translated text you require, you will need to generate a new GTAC_Translation_File for your machine. Still in the Master Translation Mapper file, scroll over to the column that contains a note indicating “Concat String for Trans Mapping File (paste to a notepad created csv file)”. Under this note, starting at the cell that shows all the languages (“English”,”Portuguese” etc), select all the cells from this point, down to the bottom of of the cells containing text. The last cell should contain Fault 1639. After you have selected the entire section of cells, right click and copy.
 ![Step 6](./GTAC%20Language%20Translation%20Images/Step%206.png)

### Step 7:
Open the GTAC_Translation_File using notepad, delete the entire current contents
 ![Step 7](./GTAC%20Language%20Translation%20Images/Step%207.png)

### Step 8: 
Paste the text you copied from step 6, confirm the correct text was copied by verifying your Last Edited line is correct. Save and close.
 ![Step 8](./GTAC%20Language%20Translation%20Images/Step%208.png)

### Step 9:
Place the GTAC_Translation_File onto your machine in the ICxx folder (you will be overwriting the older GTAC-Translation_File on your machine)
 ![Step 9](./GTAC%20Language%20Translation%20Images/Step%209.png)

### Step 10:
Confirm the translation work on the machine by selecting the appropriate language. Confirm that buttons, fault etc are displaying as expected in the selected language. If this step is successful, you are complete!
 ![Step 10](./GTAC%20Language%20Translation%20Images/Step%2010.png)
