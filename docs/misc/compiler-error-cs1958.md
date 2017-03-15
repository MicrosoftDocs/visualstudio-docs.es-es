---
title: "Error del compilador CS1958 | Microsoft Docs"
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
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1958
No se pueden aplicar expresiones de inicializador de objeto y colección a una expresión de creación de delegado.  
  
 Un delegado no tiene miembros como una clase o una estructura, por lo que no hay nada que un inicializador de objeto deba inicializar. Si se produce este error, probablemente es porque hay llaves después de la expresión de creación de delegado. Quite las llaves y este error desaparecerá.  
  
### Para corregir este error  
  
1.  Quite las llaves.  
  
## Ejemplo  
 El código siguiente produce el error CS1958:  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```