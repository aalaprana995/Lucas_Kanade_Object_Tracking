# Lucas_Kanade_Object_Tracking
This is a computer vision repository. It has Lucas Kanade Object Tracking implementation.

## Problem formulation
The main goal of the template based tracking using Lucas Kanade Method is to find the set of warp parameters "p" such that when the image  "I" is warpped using the parameters "p" it matches the templates T(x).
## Assumptions 
-  The template is tightly bounding the object to be tracked with minimal background. There are no errors in the template image.
-  There is no occlusion in the template image.
-  Brightness constancy: The intensity of the object appearance is always the same in all the frames.
## Basic concepts 
**Template warping**
- Given a template image T(x).
- Pick all pixel from the template image T(x) and warp them using the function "W(x,p)", where p are the parameters of the Affine transformation.
![Screenshot from 2021-11-07 11-30-10](https://user-images.githubusercontent.com/93336207/140653460-6b0718c2-d446-4796-80ff-e71b951cea4c.png)
**Jacobian**
## Mathematics and Calculations
To solve the Lucas Kanade Algorithm for object tracking the Sum of Squared Equation "E" needs to be minimized.
![Screenshot from 2021-11-07 11-40-14](https://user-images.githubusercontent.com/93336207/140653789-d07583f1-2a5c-4629-b594-80c6da7f6e16.png)\
For minimizing "E" we would be using Gauss-Newton Method:
- Apply a first order approximation of the warp. 
- Minimize the function iteratively until a threshold is reached.
**Steps**
- Assume that we know the initial estimate of "p".Thus, we need to find &#916; p that minimizes 
![Screenshot from 2021-11-07 11-40-14](https://user-images.githubusercontent.com/93336207/140653789-d07583f1-2a5c-4629-b594-80c6da7f6e16.png)
- Using First-order Taylor approximation of I(W(x,p+&#916; p))-T(x)) gives
![Screenshot from 2021-11-07 11-54-19](https://user-images.githubusercontent.com/93336207/140654222-e1d0e799-aa5c-4190-85df-46b6eee51e66.png)
- Replacing  I(W(x,p+&#916; p)) with the above approximation 
![Screenshot from 2021-11-07 11-56-02](https://user-images.githubusercontent.com/93336207/140654251-53525003-10d9-46ee-9fab-7f2c914f99f2.png)
- Differentiate E with respect to &#916; p and equate it to 0.
![Screenshot from 2021-11-07 11-57-54](https://user-images.githubusercontent.com/93336207/140654306-c844d1d5-0f28-4869-bbee-9e945d06a038.png)
![Screenshot from 2021-11-07 11-59-47](https://user-images.githubusercontent.com/93336207/140654390-72419272-3225-40c1-baff-48cff5888513.png)
![Screenshot from 2021-11-07 12-01-15](https://user-images.githubusercontent.com/93336207/140654426-d28e82d8-8a30-4611-9240-72b120bcf887.png)
## Algorithm
