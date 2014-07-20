## **Interpreting pixel maps**
Factors which lead to success include:

 1. Colours. Binary (black and white only) are simplest; gradients, dotted regionscan cause problems. AMI separates colours into complementary pixel maps
 2. Noise (common in scanned documents), grayscales and antialiasing (very common) mean that background / threshold levels are critical and AMI can adjust these
 3. Bleeding and cavitation. Graphics primitives which are close ofetn "bleed" into a single object and for characters we have heuristic rules
 4. Thinning. AMI reduces lines and strokes to single pixel width and then applies a topological approach
 5. Character recognition (OCR). Traditional methods don't work well with scientific characters which are often rotated, isolated, have variable fonts, italic and/bold and cover a wide range of Unicode (maths, Greek, symbols). We have developed a topological approach which is robust to distortion and scaling and can be combined with classical methods (bitwise correlation).
 6. Separation of objects. We identify objects by floodfill, by expanding borders or convex hulls. Overlap of different colours is often tractable especially where these are primitives (lines, circles); we can sometimes resolve overlapping objects by creatng a dictionary of primitives (e.g. symbols).
 7. Segmentation. AMI uses Douglas-Peuckert segmentation to approximate curved strokes and where possible tries to fit them to circles