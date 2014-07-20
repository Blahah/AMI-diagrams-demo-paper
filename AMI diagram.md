### **AMI-diagram: Mining Facts from Images**

## **Abstract**
There are at least 10 million diagrams published in the scientific literature each year and many of them represent factual information. AMI-diagramanalyzer is a flexible tool which can mine facts from diagrams and convert the data into XML. The targets include X-Y plots, barcharts, chemical structure diagrams and phylogenetic trees. AMI can ingest born-digital diagrams either as latent vectors (converted from Postscript), pixel diagrams (PNGs and JPEgs) or scanned documents. For high-quality/resolution diagrams the process is automatic; commandline parameters can be used for noisy or complex diagrams. 

## **Background**
Over 1 million scientific articles are published yearly and a similar amount of theses and grey literature. Many contain diagrams, such as graphs or domains-specifc objects, representing factual information and often this is the primary way of communication (e.g. molecular structure diagrams). Almost all the diagrams are now born digital (i.e. the output is written directly from a program to file). The programs include generic plotting packages (GNUPlot, R, Excel), specialist editors such as JChempaint or Chemdraw for molecules, or are generated directly from instruments(e.g. spectra). The plots are usually high resolution, either scalable vectors + text (such as SVG or Postscript derivatives) or large pixel maps, often between 1 million and 20 million megapixels. 

Most scientific data is never published (estimates are often > 80% loss), so extraction of data from images can be a vital source of semantic data. Traditional approaches include pencil and ruler, or cutting out peaks and weighing the paper and these are still, infrotuantely, used today. 

## Overview
We have developed image and vector processing technology which can reconstruct semantic data from a wide range of diagrams. Users may start with PDF documents, PNG or JPEG diagrams, or other sources of vectors (Word or Powerpoint EWF, Postscript, etc.). AMI is a work-in-progress being deployed to alpha-testers especially in chemistry and phylogentics. The overall process is:

 * dissect and restructure PDFs and extract images.
 * transform raw images into SVG.
 * associate SVG with extracted captions to add semantics and classification. 
 * from the SVG primitives build domain-independent mid-level graphics objects (boxes, circles, grids, annotations, symbols, etc.)
 * use domain-specific heuristics from the classification to create high-level semantic objects (x-y plots, molecular structures, phylogenetic trees, maps, etc.)

## Interpreting pixel maps
Factors which lead to success include:

 1. Colours. Binary (black and white only) are simplest; gradients, dotted regionscan cause problems. AMI separates colours into complementary pixel maps
 2. Noise (common in scanned documents), grayscales and antialiasing (very common) mean that background / threshold levels are critical and AMI can adjust these
 3. Bleeding and cavitation. Graphics primitives which are close ofetn "bleed" into a single object and for characters we have heuristic rules
 4. Thinning. AMI reduces lines and strokes to single pixel width and then applies a topological approach
 5. Character recognition (OCR). Traditional methods don't work well with scientific characters which are often rotated, isolated, have variable fonts, italic and/bold and cover a wide range of Unicode (maths, Greek, symbols). We have developed a topological approach which is robust to distortion and scaling and can be combined with classical methods (bitwise correlation).
 6. Separation of objects. We identify objects by floodfill, by expanding borders or convex hulls. Overlap of different colours is often tractable especially where these are primitives (lines, circles); we can sometimes resolve overlapping objects by creatng a dictionary of primitives (e.g. symbols).
 7. Segmentation. AMI uses Douglas-Peuckert segmentation to approximate curved strokes and where possible tries to fit them to circles

## **Reconstructing objects**
Many segmented objects are suitable for domain-specific interpretation. 
 1.  **Chemical structures** are lines and characters, with occasional circles; we often approach 100% Recall/Precison for vector or good pixel diagrams. 
 2.  **Phylogenetic trees** are often tractable, consisting of a single connected trees with labels close to the tip. We can process rooted trees (orthogonal and circular) and unrooted and for simple diagrams precision is often 100%. The diagram below is converted to the semantic Newick string: ((n122,((n121,n205),((n39,(n84, [... clipped ...] ((n53,n131),n159))))))); See http://blogs.ch.cam.ac.uk/pmr/2014/06/25/content-mining-we-can-now-mine-images-of-phylogenetic-trees-and-more/
 3.  **X-y plots**. These are often very tractable - again with high precision; they contain
  a. X- and / or Y- axes each consisting of lines with tick marks, scales, quantities and units
  b. symbols or points, perhaps with error bars and legands for each type
  c. an overall title

## **Current status**
AMI is Open-source (Apache2) in pure Java. It can be deployed as a command-line option including recursion over directories and ingestion of web streams. It ingests PDF, SVG, XML, HTML and image formats and usually takes < 1 second per image (some documents include tens of such). 

## **Acknowledgements**
PM-R thanks The Shuttleworth Foundation for a Fellowship and Grant and RM thanks BBSRC for support for the PLUTo project

