Download Link: https://assignmentchef.com/product/solved-cs180-assignment3-the-function-rasterize-triangleconst-triangle-t
<br>
In the last assignment, we drew a wire-frame triangle on the screen, which doesn’t look so interesting. This time we will move one step forward – draw solid triangles on the screen, in other words, rasterize a triangle. Last time, after the view-port transformation, we called the rasterize wireframe(const Triangle&amp; t), this time you need to implement the function rasterize triangle(const Triangle&amp; t). The general workflow inside this function is:

<ul>

 <li>Create the 2D bounding box of the triangle.</li>

 <li>Iterate through all the pixels (using their <strong>integer </strong>indices) that are inside this bounding box. Then, use the screen-space coordinate of the center of the pixel to check if the center point is inside the triangle.</li>

 <li>If it is inside, then compare the <strong>interpolated </strong>depth value at its position to the corresponding value from the depth buffer.</li>

 <li>If the current point is closer to the camera, set the pixel color and update the depth buffer.</li>

</ul>

Functions that you need to edit:

<ul>

 <li><strong>rasterize triangle: </strong>Perform the triangle rasterization algorithm, (the workflow which is mentioned above). It is located in the file cpp</li>

 <li><strong>static bool insideTriangle(int x, int y, const Vector3f* v): </strong>Test if a point is inside a triangle. You can change the definition of this function. That means, you can update the return type, or the function parameters the way you want, as mentioned this function should be called from rasterize triangle(const Triangle&amp; t). It is located in the file cpp</li>

 <li><strong>get model matrix(float rotation angle): </strong>For this assignment you don’t need to handle any rotation, just return an identity matrix. It is located in the file cpp</li>

 <li><strong>get projection matrix(float eye fov, float aspect ratio, float zNear, float zFar): </strong>This is also left empty in the file cpp. Cpoy-paste your implementation of this function from <strong>second assignment</strong>.</li>

</ul>

Since we only know the depth value at the three vertices of the triangle. For the pixels inside the triangle, we need to do the <strong>interpolation </strong>to get its depth value. We have handled this part for you, since it is the topic that has not been covered in the lecture yet. The interpolated depth value is saved in the variable z_interpolated. You can find this part of the code in the comments in the rasterize triangle(const Triangle&amp; t)

Pay attention to how we initialize the depth buffer and the sign of your z values.

Finally, we provide two hard-coded triangles to test your implementation, if you do it correctly, you will see the output image like this:

The text will not be there and also note how one triangle is on top of another. You will get an incorrect result if the depth testing part is not implemented correctly.

<ul>

 <li><strong>Getting started</strong></li>

</ul>

Download and use our updated skeleton code package either on your own machine or in the virtual machine. The dependencies are exactly the same as used in the <strong>second assignment</strong>, so make sure to follow the same steps to run the code as mentioned in the <strong>second assignment</strong>. Do note that this assignment’s skeleton is slightly different and rotation will not work, but the commands to build and run the code is exactly like how it was in <strong>second assignment</strong>(except the rotate part). Please refer to the <strong>second assignment </strong>for more instructions.