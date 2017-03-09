---
title: "Advertencia del compilador (nivel 2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS3019
La comprobación de conformidad con CLS no se realizará en 'tipo' porque no es visible desde fuera de este ensamblado.  
  
 Esta advertencia se produce cuando un tipo o un miembro que tiene el atributo <xref:System.CLSCompliantAttribute> no es visible desde otro ensamblado. Para resolver este error, quite el atributo de cualquier clase o miembro que no sea visible desde el otro ensamblado, o haga visibles el tipo o miembros. Para más información sobre la conformidad con CLS, vea [\<PAVE OVER\> Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS3019:  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## Vea también  
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)