---
title: "Advertencia del compilador (nivel 1) CS3018 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3018
El tipo 'type' no se puede marcar como conforme con CLS porque es miembro de un tipo 'type' no conforme con CLS  
  
 Esta advertencia se produce si una clase anidada con el atributo CLSCompliant establecido en `true` se declara como un miembro de una clase declarada con el atributo CLSCompliant establecido en `false`. Esto no se permite, ya que una clase anidada no puede ser conforme con CLS si es miembro de una clase externa que no es conforme con CLS. Para resolver esta advertencia, quite el atributo CLSCompliant de la clase anidada o cámbielo de `true` a `false`. Para más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS3018.  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```