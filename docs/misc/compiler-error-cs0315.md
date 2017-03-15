---
title: "Error del compilador CS0315 | Microsoft Docs"
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
  - "CS0315"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0315"
ms.assetid: 9bb1cab3-1dca-4467-978b-1ab310901a70
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0315
No se puede usar el tipo 'TipoDeValor' como parámetro de tipo 'T' en el tipo o el método genérico 'tipoOmétodo\<T\>'. No hay ninguna conversión boxing de 'TipoDeValor' a 'TipoDeReferencia'.  
  
 Este error se produce al restringir a un tipo genérico para una clase determinada e intentar construir una instancia de esa clase mediante un tipo de valor al que no se puede aplicar la conversión boxing implícitamente.  
  
### Para corregir este error  
  
1.  Una solución es volver a definir la estructura como clase.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0315:  
  
```  
// cs0315.cs public class ClassConstraint { } public struct ViolateClassConstraint { } public class Gen<T> where T : ClassConstraint { } public class Test { public static int Main() { Gen<ViolateClassConstraint> g = new Gen<ViolateClassConstraint>(); //CS0315 return 1; } }  
```  
  
## Vea también  
 [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)   
 [Conversión boxing y conversión unboxing](/dotnet/csharp/programming-guide/types/boxing-and-unboxing)