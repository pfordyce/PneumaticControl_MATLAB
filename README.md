# PneumaticControl_MATLAB
Pneumatic Control using the WAGO Modbus Controller In Matlab

To use this file, open the WAGO subfolder and change the associated IP address to be your WAGO ethernet address. 

Then use the Dummy Chip example and associated "How to Setup" sequence below to setup your own microfluidic chip. 

To do so, add your Chip file name and valve state list and location to the ChipAutomation.m file under Common. 

A fully-setup MITOMI Chip is provided as an example. 

How to Setup Your Device in MATLAB: 
o Make MatLab Program for Running Devices


1.	Go into your AutoCAD design, select all features, select “print” from the file menu, and select “Save as .eps”.
2.	Import the .eps file into Illustrator.
3.	Adjust as necessary (this generally requires ungrouping the objects, removing clipping masks, and sometimes adjusting the linewidth) and export as a .png file.
Create MatLab program to run device
4.	Transfer .png file to compute
5.	Start Matlab.
6.	Create folder for device control.
7.	Navigate to folder in Matlab and add folders and subfolders to path.
8.	Copy all files from a current control folder (e.g. MycroArrayv1p0 or PC1kv1p0) to the current folder.
9.	Change all device-specific file names (do not change ChipLocations.txt or ValveNumbers.txt).
10.	Delete existing .png file and replace with the .png file for your device.
11.	Edit runDeviceName.m file (example: runMycroArrayV1p0.m).
a.	Change the device name in the file to the new device name (all lowercase).
b.	Change scope, camera, and mfcs parameters if desired.
12.	Edit deviceName.m file (example: mycroArrayV1p0.m).
a.	Change chip name (line 1 ) to be consistent with current chip name.
b.	Change myName (line 22).
c.	Change myTag (line 23).
d.	Change image (line 128) to match .png file name.
e.	Change description (lines 243-246) – this is not really necessary.

13.	Edit Matlab_FordyceLab/Common/chipAutomation.m.

a.	Add case for chip (line 135 or so).  Case must be lowercase.  The name in chip =  must match the name of the .m file for the device.  For example, for case “mycroarrayv1p0”, it should read chip = MycroArrayV1p0(vcType, valveNumFile, virtual, true, myName);

14.	Edit ValveNumbers.txt (be sure to open this file OUTSIDE of Matlab so that the formatting characters don’t get screwed up).
a.	Valve numbering starts at 0, valves are numbered as described by stickers on banks with the lowest numbered valves closest to you.
b.	For this, you want to think of how you will physically connect the chip – it’s easiest to have valves that are located close together on the chip come from the same valve manifold.
15.	Right click on .fig file, select “Open in GUIDE”.
a.	Add or duplicate valve controls as necessary to give you the right number of valves on the device.
b.	Move the valves around until they are approximately where the control is on the chip.  This is tricky because you can’t actually see the .fig file as the background here – it’s easiest to open the .png file and kind of guess as to where the controls will be.
c.	For each valve, right click on:
i.	The valve object to change title.
ii.	The little box in the valve object that has the “x” in it.  Change the tag to be one of the names in the ValveNumbers.txt file + “Num”.  For example, if the valve name in the ValveNumbers.txt file is “In”, this should read “InNum”.
iii.	The dark box in the valve object.  For this, change the tag to be one of the names in the ValveNumbers.txt file.  In the previous example, this would read “In”.
16.	Right click on runDeviceName.m and select “Run”.

