---
title: "&#39;MyBase&#39; debe ir seguida de &#39;.&#39; y un identificador. | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyBase&#39; debe ir seguida de &#39;.&#39; y un identificador.
`MyBase` no es una variable de objeto verdadera y no puede aparecer por sí sola. Se usa solo para tener acceso a un miembro de la clase base de la instancia actual.  
  
 **Identificador de error:** BC32027  
  
### Para corregir este error  
  
-   Si desea tener acceso a miembros, especifique el operador de acceso a miembros \(.\) y un miembro de la clase base después de `MyBase`.  
  
-   Si no desea tener acceso a miembros, declare e inicialice una instancia de la clase base o quite la referencia a `MyBase`.  
  
## Vea también  
 [MyBase: eliminar](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)