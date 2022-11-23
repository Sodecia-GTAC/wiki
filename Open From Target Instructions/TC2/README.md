# Pull From Target in TC2

Start by ensuring you can ping the target:

![image](https://user-images.githubusercontent.com/56392095/203604416-f9856b37-e392-42a8-9813-6eb9430cb77a.png)

Next, create a blank folder on your Desktop for the pulled project to be placed into:

![image](https://user-images.githubusercontent.com/56392095/203596346-6f1450de-20eb-49d8-85af-0c1dc5ba0db0.png)

Open the Edit Routes Dialog to create a new route to the target:

![image](https://user-images.githubusercontent.com/56392095/203604721-672c63c6-8177-4ea8-9964-57defd68b290.png)

Select to "Add" a new route, enter the IP Address of the target and then click the "Enter Host Name / IP". The new target should show up in the dialog (arrow in screen shot below):

![image](https://user-images.githubusercontent.com/56392095/203605023-d999a64c-437b-4cf0-8601-ac16ab21aa3b.png)

Click "Add Route", this launches the Add Remote Route dialog box, enter the administrator password for the target Addministrator account, check the "TwinCAT 2.x Password Format" check box and then click Okay:

![image](https://user-images.githubusercontent.com/56392095/203605308-b6bda68b-3cdd-4e3a-8fc3-d9fb4bc68623.png)

If all went well, there should be an X under connected of your new route:

![image](https://user-images.githubusercontent.com/56392095/203605594-a4f56cff-030c-459c-a9df-42810abe26dc.png)

Close out the routing dialog boxes and open TwinCat PLC Control (TC2), in PLC Control, select to Open from Target:

![image](https://user-images.githubusercontent.com/56392095/203606393-d37f2df8-8bea-4314-b0d5-decac4fb884a.png)

First, PLC Control will ask you to chose the target system type, for all GTAC machines we can leave it as PC or CX:

![image](https://user-images.githubusercontent.com/56392095/203606701-e70432cd-44cb-4166-9eca-63922d6e848a.png)

Next, PLC Control will ask to choose the target runt time system, choose Port 801 from the target that we just created the new route for, then click "OK":

![image](https://user-images.githubusercontent.com/56392095/203607021-33c215ec-4647-4611-9e91-bacb8880ae27.png)

PLC Control will attempt to gather the project information from the Target, if successful you will be left with something like this:

![image](https://user-images.githubusercontent.com/56392095/203607383-fff40f36-edb3-434e-8959-8aadccea0cc5.png)

Now we can simply save the project to the blank folder we created on our desktop. To do so, select File -> Save As and then navigate to the blank folder. Give the project a name and then hit save:

![image](https://user-images.githubusercontent.com/56392095/203608065-607bbdb8-0465-479c-9ba7-f9023bf22955.png)



You now have a backup copy of the PLC program from the Target. Great Work!





