---
title: "Advertencia del compilador (nivel 1) CS1957 | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1957
El miembro 'name' invalida 'method'. Hay varios candidatos de invalidación en tiempo de ejecución. El método que se llamará depende de la implementación.  
  
 No se pueden diferenciar en tiempo de ejecución los parámetros de método que solo varían por que sean `ref` o `out`.  
  
### Para evitar esta advertencia  
  
1.  Asigne a uno de los métodos un nombre diferente o un número diferente de parámetros.  
  
## Ejemplo  
 El código siguiente genera el error CS1957:  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```