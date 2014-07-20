## **Reconstructing objects**
Many segmented objects are suitable for domain-specific interpretation. 

 1. **Chemical structures** are lines and characters, with occasional circles; we often approach 100% Recall/Precision for vector or good pixel diagrams. The diagram below is a photograph of a poster and shows varying backgrounds, line broadening and skewing. In spite of this it is automatically converte to a semantic molecule with formula C18 H18 N3 O in under a second. We have successfully converted thousands of molecules, with annotations, and also chemical reactions into Chemical Markup Language
 2. **Phylogenetic trees** are often tractable, consisting of a single connected trees with labels close to the tip. We can process rooted trees (orthogonal and circular) and unrooted and for simple diagrams precision is often 100%.The circular tree below is separated from its characters and converted to the semantic Newick representation 
 3. **X-y plots**. These are often very tractable - again with high precision; they contain:
 
  *  X- and / or Y- axes each consisting of lines with tick marks, scales, quantities and units
  *  symbols or points, perhaps with error bars and legands for each type
  * an overall title
