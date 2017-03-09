---
title: "Advertencia del compilador (nivel 1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1911
El acceso al miembro 'nombre' a través de una palabra clave 'base' desde un método anónimo, expresión lambda, expresión de consulta o iterador genera código no comprobable. Considere la posibilidad de mover el acceso a un método auxiliar en el tipo contenedor.  
  
 Llamar a funciones virtuales con la palabra clave `base` dentro del cuerpo de método de un iterador o métodos anónimos generará código no comprobable. El código no comprobable no se ejecutará en un entorno de confianza parcial.  
  
 Una solución para la advertencia CS1911 es mover la llamada de función virtual a una función auxiliar.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1911.  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```