---
title: "Se esperaba &#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; o &#39;Const&#39; | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; o &#39;Const&#39;
Una línea de código fuente comienza con un carácter `#`, pero una directiva de compilación condicional válida no sigue inmediatamente a `#`. Las directivas válidas incluyen `#Const`, `#ExternalSource`, `#If`, `#Else`, `#ElseIf`, `#End If` y `#Region`.  
  
 **Identificador de error:** BC30248  
  
### Para corregir este error  
  
1.  Asegúrese de que la directiva de compilación condicional esté escrita correctamente.  
  
2.  Asegúrese de que no hay ningún espacio intermedio entre el carácter `#` y la directiva.  
  
3.  Quite el carácter `#` o agregue una directiva válida inmediatamente después de este.  
  
## Vea también  
 [Directivas](/dotnet/visual-basic/language-reference/directives/directives)