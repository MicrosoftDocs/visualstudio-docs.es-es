---
title: "La expresi&#243;n es del tipo &#39;&lt;typename&gt;&#39;, que no es un tipo de colecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La expresi&#243;n es del tipo &#39;&lt;typename&gt;&#39;, que no es un tipo de colecci&#243;n
La variable de grupo especificada en una instrucción `For Each` no es un objeto de colección ni una matriz, y su tipo no implementa la interfaz <xref:System.Collections.IEnumerable>. El tipo debe admitir el patrón de diseño de colección [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o implementar <xref:System.Collections.IEnumerable>.  
  
 **Id. de error:** BC32023  
  
### Para corregir este error  
  
-   Declare la variable de grupo para que sea de un tipo de clase que admita el diseño de colección [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o implemente <xref:System.Collections.IEnumerable>.  
  
## Vea también  
 <xref:System.Collections.IEnumerable>   
 [For Each...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Clase de colección de Visual Basic](http://msdn.microsoft.com/es-es/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)