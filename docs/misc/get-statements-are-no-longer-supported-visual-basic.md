---
title: "Ya no se admiten instrucciones &#39;Get&#39; (Visual Basic) | Microsoft Docs"
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
  - "vbc30767"
  - "bc30767"
helpviewer_keywords: 
  - "BC30767"
ms.assetid: 6aa62dcc-99aa-4051-a81e-3bbb6a8c355f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten instrucciones &#39;Get&#39; (Visual Basic)
Ya no se admiten instrucciones `Get`. La funcionalidad de E\/S de archivos está disponible normalmente en el espacio de nombres `Microsoft.VisualBasic`, pero la versión de destino de .NET Compact Framework no la admite.  
  
 **Id. de error:** BC30767  
  
### Para corregir este error  
  
-   Realice operaciones de archivo con funciones definidas en el espacio de nombres <xref:System.IO>.  
  
## Vea también  
 <xref:System.IO>   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Acceso a archivos con Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)