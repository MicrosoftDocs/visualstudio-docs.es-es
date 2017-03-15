---
title: "Los valores de &#39;&lt;typename&gt;&#39; no se puede convertir en &#39;Char&#39; | Microsoft Docs"
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
  - "bc32007"
  - "vbc32007"
helpviewer_keywords: 
  - "BC32007"
ms.assetid: b04212da-57ac-4493-9480-04c12b50f875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los valores de &#39;&lt;typename&gt;&#39; no se puede convertir en &#39;Char&#39;
Los valores de '\<typename\>' no se puede convertir en Char. Use 'Microsoft.VisualBasic.ChrW' para interpretar un valor numérico como carácter Unicode o conviértalo primero en 'String' para producir un dígito.  
  
 Una expresión intenta convertir un tipo de datos distinto de `String` o `Object` en `Char`.  
  
 **Identificador de error:** BC32007  
  
### Para corregir este error  
  
-   Use la función `ChrW` para convertir un valor numérico en un carácter Unicode, o convierta primero el valor a `String` y luego a `Char`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Funciones Chr, ChrW](http://msdn.microsoft.com/es-es/37f3c707-8a6f-4c51-9b02-9e634c4299ab)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Char \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/char-data-type)