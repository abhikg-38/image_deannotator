For the task of partial de annotation, I used the following methods and approaches:

-I started by resizing the image and converting the colored image to a gray scale image

-I then applied contrast enhancement using Clahe to make the the boundaries of the annotations stand out. Experimented with different clipLimit parameters
 
-I employed GaussianBlur to blur out the noise, used a 5x5 kernel size with SD=0

-I applied Canny edge detection and experimented with different threshold parameter for the edges
 
-Further applied edge dilation of connect the broken edges and make them stand out for effective edge detection
 
-I extracted the contours of the edge image, used RETR_LIST to obtain all of the contours
 irrespective of nesting hierarchy
 
-For filtering contours of the dog annotation, I used a two pronged approach: 
 I initially applied a rectangle to every contour as the concerned annotation is box shaped. The rectangular frames having an acceptable aspect ratio are filtered.
 After this, I sorted these filtered contours on the basis of their collective area and the largest was chosen as the annotation to be removed.
 
-I overlaid the extracted contours over the original images. Used a black mask and overlaid white contour demarcation over it. For the last step, I used TELEA INPAINT mechanism to retain the underlying structure of the image after de annotation
