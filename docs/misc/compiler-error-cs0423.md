---
title: "Error del compilador CS0423 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0423"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0423"
ms.assetid: e4ec44b6-bf9c-41f7-a309-8f8b9e325691
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0423
Dado que 'clase' tiene el atributo ComImport, 'método' debe ser extern o abstract.  
  
 La especificación del atributo ComImport implica que la implementación de la clase se importará de un módulo COM. No se pueden definir métodos adicionales.  
  
 El ejemplo siguiente genera la advertencia CS0423:  
  
```  
// CS0423.cs using System.Runtime.InteropServices; [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class ImageProperties { public static void Main()  // CS0423 { ImageProperties i = new ImageProperties(); } }  
```