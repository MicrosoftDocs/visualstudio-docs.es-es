---
title: "Error del compilador CS0540 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0540"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0540"
ms.assetid: 2da2cd4a-0ff1-45ea-bb72-ea078bc95dea
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0540
'miembro de la interfaz': el tipo contenedor no implementa la interfaz 'interfaz'  
  
 Se intentó implementar un miembro de interfaz en una [clase](/dotnet/csharp/language-reference/keywords/class) que no se deriva de la [interfaz](/dotnet/csharp/language-reference/keywords/interface). Debe eliminar la implementación del miembro de interfaz o agregar la interfaz a la lista de clases base de la clase.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0540.  
  
```  
// CS0540.cs interface I { void m(); } public class Clx { void I.m() {}   // CS0540 } // OK public class Cly : I { void I.m() {} public static void Main() {} }  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0540.  
  
```  
// CS0540_b.cs using System; class C { void IDisposable.Dispose() {}   // CS0540 } class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```