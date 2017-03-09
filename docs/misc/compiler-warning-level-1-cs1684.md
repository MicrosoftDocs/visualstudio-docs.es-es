---
title: "Advertencia del compilador (nivel 1) CS1684 | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1684
La referencia al tipo 'Nombre de tipo' indica que está definida en 'Espacio de nombres', pero no se pudo encontrar  
  
 Este error puede deberse a la existencia de una referencia dentro de un espacio de nombres que hace referencia a un tipo que dice existir dentro de un segundo espacio de nombres, pero no es así. Por ejemplo, mydll.dll indica que el tipo `A` existe dentro de yourdll.dll, pero no es así. Una posible causa de este error es que la versión de yourdll.dll que se usa es demasiado antigua y no se ha definido `A`.  
  
 El ejemplo siguiente genera la advertencia CS1684.  
  
## Ejemplo  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## Ejemplo  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## Ejemplo  
 Volvemos a generar ahora el primer ensamblado, omitiendo la definición de la clase C2 para que no se defina en la recompilación.  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## Ejemplo  
 Este módulo hace referencia al segundo módulo mediante el identificador `Ref`. Sin embargo, el segundo módulo contiene una referencia a la clase `C2`, que ya no existe debido a la compilación del paso anterior y, por lo tanto, se devuelve el mensaje de error CS1684 al compilar este módulo.  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```