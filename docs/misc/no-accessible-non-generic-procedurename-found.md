---
title: "Se encontr&#243; &#39;&lt;procedurename&gt;&#39; no gen&#233;rico al que no se puede obtener acceso | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se encontr&#243; &#39;&lt;procedurename&gt;&#39; no gen&#233;rico al que no se puede obtener acceso
Una instrucción llama a un procedimiento que tiene más de una versión sobrecargada, pero todas las versiones sobrecargadas que son genéricas y la llamada no proporciona argumentos de tipo.  
  
 Si hay solo una versión genérica y se llama sin argumentos de tipo, el compilador puede intentar realizar la *inferencia de tipos*. Para más información, vea "Inferencia de tipos" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Sin embargo, si hay más de una versión genérica, el compilador no será capaz de elegir entre ellas a menos que proporcione los argumentos de tipo. Si se proporciona un argumento de tipo, debe proporcionar un argumento de tipo para cada parámetro de tipo definido por una de las versiones sobrecargadas.  
  
 **Identificador de error:** BC32117  
  
### Para corregir este error  
  
-   Llame al procedimiento con una lista de argumentos de tipo.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)