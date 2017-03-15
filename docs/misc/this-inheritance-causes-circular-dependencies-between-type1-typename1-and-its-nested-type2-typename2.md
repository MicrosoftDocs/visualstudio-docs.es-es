---
title: "Esta herencia produce dependencias circulares entre &lt;tipo1&gt; &#39;&lt;nombreDeTipo1&gt;&#39; y su &lt;tipo2&gt; &#39;&lt;nombreDeTipo2&gt;&#39; anidado | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esta herencia produce dependencias circulares entre &lt;tipo1&gt; &#39;&lt;nombreDeTipo1&gt;&#39; y su &lt;tipo2&gt; &#39;&lt;nombreDeTipo2&gt;&#39; anidado
Una estructura de herencia da como resultado una dependencia circular entre clases anidadas, es decir, dos clases que heredan entre sí.  
  
 El código siguiente puede generar este mensaje de error.  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 En el código anterior, la clase `c1` hereda de la clase `c4`, pero `c4` está anidada dentro de `c3`, que hereda de `c2`, anidada dentro de `c1`.  
  
 **Identificador de error:** BC30907  
  
### Para corregir este error  
  
-   Cambie la estructura de herencia para que no haya ninguna dependencia circular.  
  
## Vea también  
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)