# Pull From Target in TC3

Start by ensuring you can ping the target:

![ping](https://user-images.githubusercontent.com/56392095/203578402-c30cf006-c494-4d3a-bc03-4a3427c20f00.jpg)

Next, create a blank folder on your Desktop for the pulled project to be placed into:

![image](https://user-images.githubusercontent.com/56392095/203596346-6f1450de-20eb-49d8-85af-0c1dc5ba0db0.png)

Open the Edit Routes Dialog to create a new route to the target:

![image](https://user-images.githubusercontent.com/56392095/203596828-78ecf8fd-72e5-4745-a322-623be9f35a5b.png)

Select to "Add" a new route, enter the IP Address of the target and then click the "Enter Host Name / IP. The new target should show up in the dialog (arrow in screen shot below):

![image](https://user-images.githubusercontent.com/56392095/203597489-3c477827-2a73-4676-9421-b1798a12fe27.png)

Click "Add Route", this launches the Add Remote Route dialog box, enter the administrator password for the target Addministrator account and then click Okay:

![image](https://user-images.githubusercontent.com/56392095/203598078-e74c6267-c2e1-4ad4-ae44-e04f3c3f0bc0.png)

If all went well, there should be an X under connected of your new route:

![image](https://user-images.githubusercontent.com/56392095/203598368-d5ea1dd3-e914-42d3-9427-4321c787345e.png)

Close out the routing dialog boxes and open XAE Shell, in XAE Shell, select to Open from Target:

![image](https://user-images.githubusercontent.com/56392095/203598755-d5ebec73-db60-4220-84e5-9c36344c461f.png)

When XAE asks to choose the target system, choose the target that we just created the new route for, then click "OK":

![image](https://user-images.githubusercontent.com/56392095/203599315-eb32c445-e49f-4676-aef3-ad38f4334e0f.png)

XAE will attempt to gather the project information from the Target and then will ask you where you'd like to place this, select the new Blank folder we created on our desktop:

![image](https://user-images.githubusercontent.com/56392095/203599780-612b8b24-8f59-4c06-8a53-7b4afaedfeb5.png)

It will again take a bit for XAE to transfer all the files from the Target to the project but you should be left with something like this:

![image](https://user-images.githubusercontent.com/56392095/203600187-57d8c4a4-63b2-4418-9b84-aea872820a33.png)

Click Save all and you now have a backup copy of the PLC program from the Target.
Great Work!








