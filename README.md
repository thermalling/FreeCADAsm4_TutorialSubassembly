Phone Assembly Tutorial
===============

A simple subassembly task using the FreeCAD Assembly 4 Workbench
----------------

Our phone will be a very simple design, with a rectangular frame, a screen, and two identical cameras:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-22-36.png)![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-23-22.png)



![](FreeCADSubAssyImages/Screenshot_2020-05-02_15-44-44.png)

During the tutorial, we will create the following files:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-14-04.png)

Two of these are assembly files, as the camera will be included as a sub-assembly in the phone in two different places, front and rear.  Assemblies, sub-assemblies and parts are handled in exactly the same way.

Saving the components in separate files allows them to be worked on by different engineers. Each will have a clearly defined interface to the other documents, allowing easy interchange of different or upgraded designs for modular components.

Setup:
===========
We need a recent version of FreeCAD (at least 0.19).
Under Tools -> Addon manager, install the Assembly4 Workbench:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_17-26-48.png)

----------------------------

Create the frame:
=========================

From the start page of FreeCAD, select "Create new..."

![](FreeCADSubAssyImages/Screenshot_2020-05-02_15-31-48.png)

Save the file in your selected directory as "*Frame*"

Choose the Assembly 4 workbench ![](FreeCADSubAssyImages/Screenshot_2020-05-02_15-58-34.png) and create a new Body: ![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-02-11.png)  Leave the default name "Body".

Now we are ready to model the frame.
In this case, it will be a simple rectangular pad with pockets for the screen and two cameras.

Right-click on the Body in the tree and select "Toggle active Body".

![](FreeCADSubAssyImages/FrameBodyRightClick.png)

This will open the Part Design workbench. ![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-05-47.png)

Create a new sketch:

![](FreeCADSubAssyImages/Screenshot_2020-05-08_15-28-41.png)

Select the XY Plane:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-07-00.png)

and click OK.

Create a rectangle 145x70mm:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-09-53.png)

Press Escape, or the close button on the Tasks tab to close the sketch.

Pad the sketch to create the frame of the phone:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-12-10.png)
Leave the default 10mm and click OK.

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-13-54.png)

Click the top face of the phone frame, then the "Create a new sketch" button. ![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-16-36.png)

Set the dimensions of the screen as follows:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-22-26.png)

**Note:** Good engineering practice would reference these dimensions from a spreadsheet to enable rapid design upgrades or different phone sizes from the same design.

Press Escape or Close to exit the sketch, and then create a pocket ![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-25-47.png)

Make the pocket 2mm deep.

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-27-01.png)

Open a new sketch on the top of the phone for the front camera cutout, and create a circle with the following dimensions:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-35-13.png)

As before, create a pocket, this time 4mm deep:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-37-02.png)

Flip the phone frame over, and repeat for the rear-facing camera, creating another 4mm deep pocket:

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-41-36.png)

![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-42-23.png)

The Tree for the *Frame* should now look like this:

![](FreeCADSubAssyImages/TreeFrame.png)

The frame design is now complete, but we need some local co-ordinate systems to allow assembly of the components to the frame in the correct places.


Create a Local Co-ordinate System for the Screen
-------------------


Switch back to Assembly 4 workbench. ![](FreeCADSubAssyImages/Screenshot_2020-05-02_15-58-34.png)

This is the heart of Assembly 4.  We will add the Local Co-ordinate Systems to the frame in the positions and orientations for the sub-assembly parts to attach correctly to the frame.

First, we will create an LCS to attach the screen in the corner of the frame. Select the **Body** in the tree ![](FreeCADSubAssyImages/TreeFrameBodySelected.png)  and then click "Create a new co-ordinate system in part"
![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-30-49.png)

Call it LCSScreen:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-00-35.png)

Right-click on the new LCS in the tree

![](FreeCADSubAssyImages/TreeFrameLCSScreenSelected.png)

and select "Edit datum".

Highlight "XY tangent to surface"

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-17-20.png)

Zoom in on the bottom left corner of the frame, and select the base plane of the pocket created earlier.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-16-02.png)

Next, click exactly in the corner of the pocket to select the vertex that will lock in the X and Y for this datum:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-19-23.png)

Note the small yellow dot in the image above.

We now have an LCS positioned correctly, but it is facing out from the corner, so we need to rotate it.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-21-24.png)

In the bottom of the dialogue, change "Around z-axis" to 180&deg;:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-22-37.png)

The LCS is now correctly oriented for the screen to attach.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-23-54.png)

Click OK at the top of the dialogue and move to the front camera position.

Create a Local Co-ordinate System for the front camera assembly
-------------------

Again, select the **Body** in the tree and click "Create a new co-ordinate system in part"
![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-30-49.png)

Name it LCSFrontCamera.

Right-click on the new LCS in the tree and select "Edit datum".

Select the bottom circumference of the front camera pocket (yellow line in this picture):

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-32-47.png)

Click OK.

That's it.  We don't need to consider rotation in this case, and the module has automatically selected "concentric" as the constraint type.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-35-45.png)


Create a Local Co-ordinate System for the rear camera assembly
-------------------

Repeat the exercise above for the rear camera:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_15-38-23.png)

Save the *Frame* file.

---------------

Create the screen:
==================
Open a new file and save it as *Screen*

Choose the Assembly 4 workbench ![](FreeCADSubAssyImages/Screenshot_2020-05-02_15-58-34.png) and create a new Body: ![](FreeCADSubAssyImages/Screenshot_2020-05-02_18-02-11.png)  Leave the default name "Body".

Right-click on the Body in the model tree and select "Toggle active body" to open the Part Design workbench.

Create a new sketch on the XY plane with a simple rectangle:  

![](FreeCADSubAssyImages/Screenshot_2020-05-15_14-42-54.png)

Note that the corner of the sketch is co-incident with the origin.  This will align later with the LCS that we created above.

Exit the sketch, then create a pad ![](FreeCADSubAssyImages/Screenshot_2020-05-09_17-01-48.png) 1mm vertically.

Right-click on the Body in the model tree, then change the appearance to 70% transparency, and a blue-ish colour.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_14-49-07.png)

Save the Screen file.

------------------

Create the camera bezel:
================

Open a new file and save it as *Bezel*.

Create a new body ![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-48-13.png) under the Assembly 4 workbench.

Right-click on the Body in the model tree and select "Toggle active body" to open the Part Design workbench.

Create a new sketch on the XY plane with two concentric circles 8mm and 6mm diameter:  

![](FreeCADSubAssyImages/Screenshot_2020-05-09_17-00-34.png)

Exit the sketch, then pad ![](FreeCADSubAssyImages/Screenshot_2020-05-09_17-01-48.png) 5mm vertically.

![](FreeCADSubAssyImages/Screenshot_2020-05-09_17-02-32.png)

--------------

Create a Local Co-ordinate System for the front camera assembly
-------------------

We now need to insert a Local Co-ordinate System to attach the lens when we create the *Camera* sub-assembly.
The lens will be positioned near the top of the bezel.

Select the **Body** in the model tree and click "Create a new co-ordinate system in part"
![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-30-49.png) under the Assembly 4 workbench.

Name it LCS\_LensAttachment:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-32-46.png)

Right-click on the new LCS in the tree

![](FreeCADSubAssyImages/TreeBezelLCSSelectid.png)

and select "Edit datum".
Select the top circumference to place the datum at the top of the bezel.

![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-36-22.png)

To protect the lens, we need to recess it 1mm below the top of the bezel.  Change "In z-direction" to -1 mm:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-38-56.png)

This drops the LCS as shown:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-39-43.png)

Save the *Bezel* file.

--------------------

Create the camera lens:
================
Open a new file, and save as *Lens*.
Create a body as before, then make a spherical lens starting with the following sketch on the **XZ** Plane, not the XY plane as for the previous parts:

![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-03-46.png)

Note that the center of the radius must be constrained vertically to the origin for a tangential top surface.
The exact dimensions are not important for this exercise.

Revolve ![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-25-55.png) the sketch 360&deg;, then mirror ![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-26-42.png)  the Revolution feature

![](FreeCADSubAssyImages/MirrorRevolution.png)

 to create a double-sided lens something like this:
 
![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-21-41.png)

You can adjust colours and transparency if you like.

For this component, we have modelled with the origin at the centre of mass, so we don't need to add an extra Local Co-ordinate System.

Our lens model tree should now look like this:

![](FreeCADSubAssyImages/TreeLensRevolvedMirrored.png)

Save the *Lens* file.

----------------------

Create the camera sub-assembly:
===============================

Create a new file, and save it as *Camera*.

Create a new Assembly 4 **Model**. ![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-47-08.png)  In this case, we don't need a Body, as we will link the bodies from the parts already created.

Prior to linking bodies from other parts, we need to close and re-open all files so that part names are shown correctly.

Insert a link to the *Bezel* body ![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-18-31.png), keeping the default name *Bezel\_Body*, since there will be only one instance of it in this sub-assembly.

![](FreeCADSubAssyImages/InsertBezel.png)

Select **Bezel\_Body** in the model tree and click "Move/Attach a part in the assembly" ![](FreeCADSubAssyImages/MoveAttachPart.png) under the Assembly 4 workbench.

For "Attach to:", select "Parent Assembly".
Select "LCS_Origin" on both sides of the dialogue:

![](FreeCADSubAssyImages/PlaceBezel.png)

This will place the bezel at the origin of the sub-assembly.

Now insert the *Lens#Body* into the *Bezel* ![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-18-31.png) in the same way, except in this case, we will attach it to the LCS created earlier.
Select "Bezel" on the right-hand side of the dialogue this time, and "LCS_LensAttachment" in the parent:

![](FreeCADSubAssyImages/PlaceLens.png)

The lens is now positioned with it's origin 1mm below the top of the bezel:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-49-06.png)

Save the *Camera* sub-assembly file.

--------------------------

Create the phone assembly:
=========================
Create a new file, and save it as *Phone*.

Create a new Assembly 4 model. ![](FreeCADSubAssyImages/Screenshot_2020-05-09_16-47-08.png)

Insert a link to the *Frame* part ![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-18-31.png), keeping the default name *Frame\_Body*, since there will be only one instance of it in this assembly.

![](FreeCADSubAssyImages/InsertFrame.png)

The frame will be inserted at the origin, so there is no need to place it.

Insert a link to the *Screen* body ![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-18-31.png), keeping the default name *Screen\_Body*, since there will be only one instance of it in this assembly.

![](FreeCADSubAssyImages/InsertScreen.png)


Place ![](FreeCADSubAssyImages/MoveAttachPart.png) the *Screen#Body* by selecting "LCS\_0" for the Screen, and "LCS\_Screen" for the co-ordinate system in the frame.

![](FreeCADSubAssyImages/PlaceScreen.png)

Because we aligned the LCS in the *Frame* file, it positions correctly without any rotation:

![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-00-54.png)

------------------

Now we can insert two instances of the *Camera* sub-assembly.

As above, insert a link to the *Camera* part ![](FreeCADSubAssyImages/Screenshot_2020-05-15_13-18-31.png), but this time, **Change** the name to *CameraFront*, since there will be two instances of it in the phone assembly.

![](FreeCADSubAssyImages/InsertCamera.png)

Place the part, choosing "LCS\_Origin" for the camera linked part, which is located at the base of the sub-assembly, and "LCS\_FrontCamera" for the parent part.

![](FreeCADSubAssyImages/PlaceCamera.png)

![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-07-14.png)

Repeat for the rear camera, selecting the same model, but this time naming it to "**CameraRear**" and selecting "LCS\_RearCamera" as the attachment point on the frame.

![](FreeCADSubAssyImages/InsertCameraRear.png)

![](FreeCADSubAssyImages/PlaceCameraRear.png)

![](FreeCADSubAssyImages/Screenshot_2020-05-15_16-08-27.png)

Our model tree now looks like this, showing **Bodies** attached from the simple parts, and **Models** from the sub-assemblies.

Save the *Phone* assembly file.
_____________________

We now have a very stylish smartphone, ready for the day when the "square" look comes back into fashion.

This model attaches subassemblyies at their origin.  For a quick tutorial on subassemblies with their own Local Co-ordinate Systems, refer to https://github.com/thermalling/FreeCADAsm4_TutorialSubassemblyTable.

Thanks to Zolko for Assembly 4, and the FreeCAD developers for making this possible for us.

All feedback and corrections most welcome.
