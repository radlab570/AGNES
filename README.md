# AGNES
**AGNES** -- animated gesture and natural expression system -- is a tool for implementing virtual puppeteering in Unreal Engine 5 using VR controllers.  This article will walkthrough the workflow for setting up the puppets in an VR Unreal project.

### Highlights
- Virtual Puppet Models: Models that are rigged to have its mouth opened and closed.
- Virtual Reality: Use the controllers to move the puppets in Unreal Engine and pull the triggers to open the mouths of the puppet on the corresponding hand.

## Prerequisites
 1. VR project in Unreal Engine 5.5
 2. "Puppet.zip" file from this repo containing the files necessary for the puppets.

## Steps For Implementing Virtual Puppets In Unreal
1. Open your VR project in Unreal. 
2. Add the "Puppet" folder to the Content Drawer.
3. Open the VRPawn Blueprint under "VRTemplate > Blueprints"
4. As shown in "VRPawn-LeftChild.png" do the following:
    - Under "MotionControllerLeftGrip" add a child actor component.
    - Name this child actor and add "ABP_Left_Puppet" actor blueprint to the child actor class.
    - Enter the transform data from the image.
5. Similarly, as shown in "VRPawn-RightChild.png" do the following:
    - Under "MotionControllerRightGrip" add a child actor component.
    - Name this child actor and add "ABP_Right_Puppet" actor blueprint to the child actor class.
    - Enter the transform data from the image.
6. For the "HandLeft" and "HandRight" skeletal meshes under "MotionControllerLeftGrip" and "MotionControllerRightGrip" do the following as shown in "VRPawn-SM.png":
    - Set "Visible" to false.
    - Set the "Skeletal Mesh Asset" to "Puppet_SkeletalMesh_More_Bones"
    - Set the "Anim Class" under "Animation" to either "AnimBP_PuppetLeft" or "AnimBP_PuppetRight" for each respective hand.
7. Under "VRTemplate > Inputs > "IA_Shoot_Right" and "IA_Shoot_Left" set the "Axis Type" to Axis1D (float).
8. Create an IMC file to map your controllers to the shoot inputs as shown in "IMC.png":
    - Create a mapping, select IA_Shoot_Right, map it to your controllers right trigger axis
    - Set Index 0 to Pulse, Trigger on Start to True, Interval to 0.01, Trigger Limit to 0, Affected by Time Dilation to False, and Actuation Threshold to 0.0
    - Do the same thing with IA_Shoot_Left and your controllers left trigger axis.
9. In the project settings, put your new IMC file in the "Enhanced Input" mapping context.

Blueprints for the left and right puppet's actor and animation blueprints are also provided in this repo.  Copy the text in the files and paste them in your blueprints if necessary.
