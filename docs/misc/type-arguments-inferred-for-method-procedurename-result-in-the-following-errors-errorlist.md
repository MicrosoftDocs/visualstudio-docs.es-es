---
title: "Los argumentos de tipo inferidos para el m&#233;todo &#39;&lt;nombreProcedimiento&gt;&#39; generan los siguientes errores: &lt;listaErrores&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los argumentos de tipo inferidos para el m&#233;todo &#39;&lt;nombreProcedimiento&gt;&#39; generan los siguientes errores: &lt;listaErrores&gt;
Se llama a un procedimiento genérico sin facilitar argumentos de tipo y los argumentos de tipo inferidos provocan una o varias infracciones de restricción.  
  
 Normalmente, cuando se invoca un tipo genérico, se facilita un argumento de tipo para cada parámetro de tipo que el tipo genérico define. Si no facilita ningún argumento de tipo, el compilador intenta inferir los tipos que se deben pasar a los parámetros de tipo. Si los tipos inferidos no satisfacen una o varias de las restricciones de parámetro de tipo, el compilador genera este error.  
  
 Una *restricción* en un parámetro de tipo limita los argumentos de tipo que se le pueden pasar. Por ejemplo, un parámetro de tipo puede restringirse para que sea una clase que implemente la interfaz <xref:System.IComparable%601>. Para más información, vea "Constraints" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Identificador de error:** BC30954  
  
### Para corregir este error  
  
-   Facilite argumentos de tipo al procedimiento genérico para que el compilador no tenga que inferirlos.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)