---
title: "Error del compilador CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0277
'clase' no implementa el miembro de interfaz 'descriptor de acceso'. 'descriptor de acceso de clase' no es público.  
  
 Este error se produce cuando se intenta implementar una propiedad de una interfaz, pero la implementación del descriptor de acceso de propiedad en la clase no es público. Los métodos que implementan miembros de interfaz deben tener accesibilidad pública. Para solucionarlo, quite el modificador de acceso del descriptor de acceso de propiedad.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0277:  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```