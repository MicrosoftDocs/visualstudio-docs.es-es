---
title: "Use &#39;FileGetObject&#39; en lugar de &#39;FileGet&#39; al usar el argumento de tipo &#39;Object&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Use &#39;FileGetObject&#39; en lugar de &#39;FileGet&#39; al usar el argumento de tipo &#39;Object&#39;.
El método `FileGet` incluye un argumento de tipo `Object`. Debe usarse `FileGetObject` en lugar de `FileGet` para evitar ambigüedades.  
  
 Tenga en cuenta que la funcionalidad que proporciona `My.Computer.Filesystem` ofrece mayor facilidad de uso y rendimiento que `FileGet` o `FileGetObject`.  
  
### Para corregir este error  
  
1.  Reemplace `FileGet` por `FileGetObject`.  
  
2.  Convierta el argumento `Object` a un tipo más específico.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Función FilePutObject](http://msdn.microsoft.com/es-es/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [My.Computer.FileSystem \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)