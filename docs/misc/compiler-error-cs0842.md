---
title: "Error del compilador CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0842
No se pueden usar propiedades implementadas automáticamente dentro de un tipo marcado con StructLayout\(LayoutKind.Explicit\).  
  
 El compilador proporciona los campos de respaldo de las propiedades implementadas automáticamente y el campo no es accesible para el código fuente. Por lo tanto, no son compatibles con <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
### Para corregir este error  
  
1.  Conviértala en una propiedad normal en la que se proporcionan los cuerpos de descriptor de acceso.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0842:  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```