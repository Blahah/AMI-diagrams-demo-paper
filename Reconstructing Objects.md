## **Reconstructing objects**
Many segmented objects are suitable for domain-specific interpretation. For example:

 1. **Chemical structures** are lines and characters, with occasional circles; we often approach 100% recall/precision for vector or good pixel diagrams. We have successfully converted thousands of molecules, with annotations, and also chemical reactions into Chemical Markup Language (e.g. figure 1a).
 2. **Phylogenetic trees** are often tractable, consisting of a single connected trees with labels close to the tip. We can process both rooted (orthogonal and circular, e.g. figure 1b) and unrooted trees. For simple diagrams precision is often 100%. 
 3. **X-y plots**. These are often very tractable (e.g. figure 1c) - again with high precision; they contain:
 
  *  X- and/or Y- axes each consisting of lines with tick marks, scales, quantities and units
  *  symbols or points, perhaps with error bars and legands for each type
  *  an overall title
