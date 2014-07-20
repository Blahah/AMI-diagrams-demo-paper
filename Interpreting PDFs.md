PDFs provide three streams:
 
1. characters with code points or their glyphs
2. paths (lines and curves)
3. pixel images

We use PDFBox from Apache (pdfbox.org) which provides these, but most STM publishers do not use Unicode fonts, and it is formally impossible to identify many character. We use a per-journal lookup which is constructed by expert classification. There is often some difficulty in identifying the pixel images and they may be layered with character codes or paths. We translate characters and paths to SVG which is an excellent intermediate format. We generally keep the images as PNGs as the SVG representation is verbose.