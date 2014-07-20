## **Overview**
Converting a semantic object to vector or pixel graphics loses most of the information. However in some domains it is possible to combine computer vision technqiues with machine-learning or rules/heuristics to recover the likely generating object. Moreover, ambiguity can often be resolved by lookup against public semantic data (e.g. dbpedia.org) or recomputing the object. We have therefore developed image and vector processing technology which can reconstruct semantic data from a wide range of diagrams. Users may start with PDF documents, PNG or JPEG diagrams, or other sources of vectors (Word or Powerpoint EWF, PostScript, etc.). AMI is a work-in-progress being deployed to alpha-testers especially in chemistry and phylogenetics.

The overall process is:

 1. dissect and restructure PDFs and extract images.
 2. transform raw images into SVG.
 3. associate SVG with extracted captions to add semantics and classification. 
 4. from the SVG primitives build domain-independent mid-level graphics objects (boxes, circles, grids, annotations, symbols, etc.)
 5. use domain-specific heuristics from the classification to create high-level semantic objects (x-y plots, molecular structures, phylogenetic trees, maps, etc.)
 
There is often an advantage in knowing the style of a journal or generating program. Collaboration is very useful here and the AMI framework is developed so that users can add in plugins (AMI uses the Visitor pattern). A Visitor can be tailored to a specific journal or domain of science. 