---
title: "La expresi&#243;n no puede aparecer dentro de un valor de atributo entrecomillado | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La expresi&#243;n no puede aparecer dentro de un valor de atributo entrecomillado
La expresión no puede aparecer dentro de un valor de atributo entrecomillado. Prueba a quitar las comillas.  
  
 Una expresión insertada en un valor de atributo de un literal XML aparece entre comillas.  
  
 **Identificador de error:** BC31155  
  
### Para corregir este error  
  
-   Quite las comillas delimitadoras del valor del atributo. A continuación se muestra un ejemplo:  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## Vea también  
 [Expresiones incrustadas en XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)