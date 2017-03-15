---
title: "Variable local no usada: &#39;&lt;localvariablename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable local no usada: &#39;&lt;localvariablename&gt;&#39;
Se ha declarado una variable local en un procedimiento, pero nunca se ha usado.  
  
 Una posibilidad es que haya un error de escritura entre las variables locales en el procedimiento. Si esta variable se usa de hecho en otra instrucción pero está escrita incorrectamente, aparecerá en el compilador como dos variables distintas.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42024  
  
### Para corregir este error  
  
1.  Compruebe los errores de ortografía en las variables locales del procedimiento. Tenga en cuenta que el uso mayúsculas y minúsculas no es relevante. Los nombres `ABC` y `abc` se tienen en cuenta para hacer referencia a la misma variable.  
  
2.  Si no hay ningún error de escritura, quite la declaración de esta variable o úsela en otra instrucción en el procedimiento.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)