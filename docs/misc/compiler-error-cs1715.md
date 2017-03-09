---
title: "Error del compilador CS1715 | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1715
'Type1': el tipo debe ser 'Type2' para que coincida con el miembro reemplazado 'MemberName'.  
  
 Este error es el mismo que [Error del compilador CS0508](../misc/compiler-error-cs0508.md), salvo que CS0508 ahora solo se aplica a los métodos que tienen tipos de valor devuelto, mientras que CS1715 se aplica a propiedades e indizadores que solo tienen 'tipos' en lugar de 'tipos de devolución'.  
  
## Ejemplo  
 El código siguiente genera el error CS1715.  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```