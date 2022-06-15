# Experiment-02-Introduction-to-Roboanalyzer-
## AIM: 
To Design & simulate an environment for pick & place operations with Industrial Robot using Robo DK software
### COMPONENTS REQUIRED:
1.	RoboDK

### THEORY: 

 Types of pick and place robots
There are several pick and place robot types and components, including:

Robotic arm – Robotic arms are the most common type of pick and place robots. A 5-axis robotic arm robot can be used for standard pick and place applications where objects are picked up and moved to other locations in a single plane. A 6-axis robotic arm robot is used for more complex applications, such as when objects must be twisted or re-oriented before being placed in another location.
Cartesian – Like a 6-axis robotic arm, Cartesian robots work in multiple planes. These robots move in three orthogonal axes (X, Y and Z) using Cartesian coordinates. They can be constructed with any type of linear actuator and several types of drive mechanisms such as belt, ball or lead screw mechanisms. They typically have better positioning accuracy compared to 6-axis robotic arms.
Delta – Often used in applications where robots pick items in groups and place them in assembly patterns or containers, Delta robots have advanced vision technologies that enable them to distinguish various sizes, shapes and colors. There are several configurations of Delta robots, but most have three arms that operate on four axes. They have heavy motors affixed to a frame, with lightweight arms connected to linking rods with joints at either end of each arm (typically ball joints) to allow movement.
Fast pick – Fast pick robots are ideal for use in medium- and high-volume applications with high-velocity SKUs. Fast pick robots fully automate the picking process, freeing up the human workforce to focus on higher-impact activities. They’re ideal for fast-moving “top-off” items, such as promotional items added to orders or batteries. These robots can pick up to 300 SKUs per hour from a pool of up to 8 SKUs.
Collaborative – Collaborative robots augment the work of humans by leading associates to pick locations and guiding associates through each task. By optimizing routes in real-time and keeping associates on task, collaborative robots help associates work more efficiently.

Applications for pick and place robots
Pick and place robots are often used in manufacturing but are also used in applications such as packaging, bin picking and inspection. Here’s a look at a few of the most common applications for pick and place robots and how they’re used.

Assembly – Pick and place robots used in assembly applications grab incoming parts from one location, such as a conveyor, and place or affix the part on another piece of the item. The two joined parts are then transported to the next assembly area.
Packaging – Pick and place robots used in the packaging process grab items from an incoming source or designated area and place the items in a packaging container.
Bin picking – Pick and place robots used in bin picking applications grab parts or items from bins. These pick and place robots typically have advanced vision systems allowing them to distinguish color, shape and size to pick the right items even from bins containing randomly mixed items. These parts or items are then sent to another location for assembly or packaging.
Inspection – Pick and place robots used for inspection applications are equipped with advanced vision systems to pick up objects, detect anomalies and remove defective parts or items by placing them in a designated location.


### PROCEDURE:
Select a robot
New robots can be added from a local drive or from the online library:

Select File Open online library (Ctrl+Shift+O). A new nested window will appear showing the online library It is also possible to select the corresponding button in the toolbar.
Use the filters to find your robot by brand, payload, ... In this example, we will use a UR10 robot (10 kg payload robot and 1.3 m reach).
Select Download. The robot should automatically appear in the station in a few seconds.
The online library can be closed once the robot is loaded Tip: Selecting reset filter in the online library will remove any filter that was use Tip: Alternatively, it is also possible to download the robot files (.robot extension) separately, from the website: http://robodk.com/library and open them in RoboDK by drag & dropping the file to the main window or by selecting FileOpen. Note: Every time a new robot is loaded in RoboDK, a new reference frame is added representing the robot base frame. Note: Loading robots from the online library will store them in the local library. The default location of this folder is: C:/RoboDK/Library/.

Add a Reference Frame
A Reference frame allows placing objects with respect to a robot or with respect to other objects in the 3D space (including position and orientation). Note: More information about reference frames in RoboDK in the reference frames section. To add a new reference frame:

Select Program Add Reference Frame Alternatively, select the equivalent button in the toolbar
Double click the reference frame (on the tree or on the 3D geometry on the main screen) to enter the coordinates shown in the image (X,Y,Z position and Euler angles for the orientation). The mouse wheel can be used on top of each case to quickly update the position of the reference frame on the main screen. The following colors are used by default: o X coordinate Red o Y coordinate Green o Z coordinate Blue o 1st Euler rotation Cyan o 2nd Euler rotation Magenta o 3rd Euler rotation Yellow Tip: Select Tools>Options>Display>Display XYZ axis letters to see the Coordinate system axes.
Select ViewMake reference frames bigger (+) to increase the size of the reference frames
Select ViewMake reference frames smaller (-) to decrease the size of the reference frames
Select ViewShow/Hide text on screen (/) to show or hide the text on the screen
Optionally, rename any reference frame or object in the tree by selecting F2

If more than one reference frame is used, it is possible to drag and drop them inside the Station Tree to match the dependency that exists in the real setup. For example, the reference Frame 2 may be placed with respect to the robot base reference. In this case, if the UR10 Base reference is moved, the Frame 2 is also moved with it. It is important to consider this if other robots or reference frames are used. The next image shows the difference in dependency.
	 
Even if the dependency is different, it is still possible to enter or retrieve the coordinates of any reference frame with respect to any other reference frame, as shown in the next image. Most robot controllers require the coordinates of the reference frame with respect to the robot base frame.

Reference frames can also be moved in the main screen by holding the Alt key, or selecting the corresponding button in the toolbar . Then, drag the reference with the mouse on the screen. As the reference is being moved, the corresponding coordinate values will be updated.

RoboDK supports most standard 3D formats such as STL, STEP (or STP) and IGES (or IGS) formats. Other formats such as WRML, 3DS or OBJ are also supported (STEP and IGES are not supported on Mac and Linux versions). To load a new 3D file:

Create Targets
Robot positions are recorded as Targets. Follow these steps to create two targets as a new home target and approach target respectively:

Double click the robot to show the robot panel
Select Paint gun as the Tool Frame. Once a tool or a reference frame becomes active it will show a green dot.
Select Frame 2 as the Reference Frame
Hold the Alt key and move the robot by dragging it through the TCP or the robot flange to a safe position, free of collisions with any objects. Alternatively, move the coordinates of the Tool Frame (TCP) with respect to the reference Frame.
Use the Other configurations section to switch between different robot configurations and make sure that none of the robot axes are close to the axis limits. Tip: In general, it is better if the first target of a program has the joint axes as centered as possible (the joint sliders are as centered as possible, as shown in the following image). This makes sure that the robot won’t reach the axis limits as it follows linear moves along the program. This is possible by changing the robot configuration.
Select Program Teach Target (Ctrl+T), or the corresponding button in the toolbar (as shown in the image). The target will be placed as a dependency of the active reference frame and will automatically remember the current robot position (cartesian and joints axes). In this example, the robot joint coordinates used for the first target are: [-150, -75, -90, -60, 70, 110] deg. These values can be copied from this text and pasted in the Joint axis jog of the robot panel using the corresponding button.

Rename the first target as Home by pressing F2. Alternatively, select ToolsRename item.
Move the robot closer to one edge of the part (by dragging the tool using the Alt key, entering coordinates or jogging the axis manually) In this example we used the following robot joint coordinates [0,0,200,180,0,180] deg.
Select Program Teach Target (Ctrl+T) or the appropriate button in the toolbar to create a new target
Rename the target to Approach as shown in step 7
Select the Home target and the Approach target alternatively to see the robot moving between the two targets
Right click the target and select Teach Current Position (Alt+double click) if a different position needs to be recorded for one of the targets
Right click the target and select Target Options… (F3) to open the target options window shown in the next image
	 
## SIMULATION

![Screenshot (98)](https://user-images.githubusercontent.com/75234588/173732290-ba488098-0c26-46dd-8741-7832ba82217d.png)

![Screenshot (99)](https://user-images.githubusercontent.com/75234588/173732301-0bbc75e7-51d6-43cd-aa3c-d47fccb35a82.png)

![Screenshot (100)](https://user-images.githubusercontent.com/75234588/173732316-e53bdf4b-7ad3-40a2-989c-fff3efd838fe.png)

![Screenshot (101)](https://user-images.githubusercontent.com/75234588/173732321-f64d77f4-58ef-4408-ad79-6a16c34b30ea.png)

![Screenshot (102)](https://user-images.githubusercontent.com/75234588/173732698-d81bde22-be76-4bd2-80c8-9ec59d5402af.png)



### PROGRAM 
 ```python
def PICKANDPLACE():
  
  #--------------------------
  # Add your default header and subprograms here
  # For example, to drive a gripper as a program call:
  # def Gripper_Open():
  #   set_digital_output(3, 1)
  #
  # def Gripper_Close():
  #   set_digital_output(3, 0)
  #
  # Example to drive a spray gun:
  def SprayOn(value):
    # use the value as an output:
    DO_SPRAY = 5
    if value == 0:
      set_digital_output(DO_SPRAY, 0)
    else:
      set_digital_output(DO_SPRAY, 1)

  #--------------------------
  
  
  # Main program:
  # Program generated by RoboDK v5.4.1 for Doosan Robotics M1013 on 15/06/2022 09:11:24
  # Using nominal kinematics.
  set_ref_coord(set_user_cart_coord(posx(-488.144,228.250,-8.358,0.0000,0.0000,0.0000),ref=DR_BASE))
  # TCP: posx(0.000,0.000,130.000,0.0000,0.0000,0.0000)
  set_tcp("Gripper RobotiQ 85 Opened")
  movej(posj(-24.078800,-17.897700,-124.071000,-2.095650,-41.137200,-18.859600))
  movej(posj(-24.155100,-20.458800,-125.034000,-2.265630,-37.614100,-18.719200))
  # Attach to Gripper RobotiQ 85 Opened
  movej(posj(-22.989800,0.006575,-93.069600,-1.319590,-90.049300,-19.351600))
  movej(posj(25.761700,1.899600,-94.921100,1.468490,-90.023500,25.584400))
  movej(posj(27.046400,-17.129900,-126.619000,2.426700,-39.288100,24.988500))
  # Detach from Gripper RobotiQ 85 Opened
  # End of main program
  
PICKANDPLACE()
```
### RESULTS :  
Thus, an environment for pick & place operations with Industrial Robot using Robo DK software is designed and simulated.
