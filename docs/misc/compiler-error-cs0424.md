---
title: "Error del compilador CS0424 | Microsoft Docs"
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
  - "CS0424"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0424"
ms.assetid: 09ae482c-255a-4f99-8dc8-ba31c3ea8c71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0424
'class': una clase con el atributo ComImport no puede especificar ninguna clase base  
  
 La especificación del atributo <xref:System.Runtime.InteropServices.ComImportAttribute> implica que la implementación de la clase se importará de un módulo COM. No se pueden agregar métodos adicionales ni campos heredados de la clase base a la implementación definida en el módulo COM.  
  
 El ejemplo siguiente genera la advertencia CS0424:  
  
```  
// CS0424.cs // compile with: /target:library using System.Runtime.InteropServices; public class A {} [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class B : A {}   // CS0424 error  
```