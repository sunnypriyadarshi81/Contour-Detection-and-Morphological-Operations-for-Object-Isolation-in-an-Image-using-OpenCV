Point-by-point explanation of the code:

    Image Reading:
        The image 'redSeaBream.png' is loaded using cv2.imread(), which reads the image in BGR format.

    Image Blurring:
        A Gaussian blur is applied with a kernel size of (5, 5) to reduce noise and smooth the image.

    Color Space Conversion:
        The blurred image is converted from BGR to HSV color space using cv2.cvtColor() to facilitate color-based segmentation.

    Color Thresholding:
        A color mask is created to isolate pixels within a specific HSV range (orange color range defined by lower_orange and upper_orange).

    Morphological Operations:
        Dilation:
            Performed twice to expand the white areas in the mask, helping close small gaps and connect disjointed areas.
        Erosion:
            Performed three times to shrink the white areas, helping to remove small noise and separate connected objects.

    Contour Detection:
        Contours are detected in the processed binary image using cv2.findContours(), focusing on external contours only.

    Filtering Contours:
        Contours are filtered by area, keeping only those with an area greater than 1000 pixels to remove small, irrelevant contours.

    Creating and Applying a New Mask:
        A new mask is created, and the filtered contours are drawn onto it. This mask is then used to isolate the desired objects from the original processed image.

    Displaying the Result:
        The final image, showing only the desired isolated objects, is displayed using Matplotlib's imshow() function in grayscale.

This sequence of steps isolates objects of a specific color range from an image, effectively using color thresholding, morphological operations, and contour detection.
