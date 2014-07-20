## **Overview**
We have developed image and vector processing technology which can reconstruct semantic data from a wide range of diagrams. Users may start with PDF documents, PNG or JPEG diagrams, or other sources of vectors (Word or Powerpoint EWF, Postscript, etc.). AMI is a work-in-progress being deployed to alpha-testers especially in chemistry and phylogentics. The overall process is:

 * dissect and restructure PDFs and extract images.
 * transform raw images into SVG.
 * associate SVG with extracted captions to add semantics and classification. 
 * from the SVG primitives build domain-independent mid-level graphics objects (boxes, circles, grids, annotations, symbols, etc.)
 * use domain-specific heuristics from the classification to create high-level semantic objects (x-y plots, molecular structures, phylogenetic trees, maps, etc.)