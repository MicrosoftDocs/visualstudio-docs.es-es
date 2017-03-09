---
title: "Advertencia del compilador (nivel 1) CS3017 | Microsoft Docs"
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
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3017
No se puede especificar el atributo CLSCompliant en un módulo que sea distinto del atributo CLSCompliant del ensamblado  
  
 Esta advertencia aparece si tiene un atributo CLSCompliant de ensamblado que entra en conflicto con un atributo CLSCompliant de módulo. Un ensamblado conforme a CLS no puede contener módulos que no son conformes a CLS. Para resolver esta advertencia, asegúrese de que los atributos CLSCompliant de módulo y de ensamblado son ambos verdaderos o falsos, o quite uno de los atributos. Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3017:  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```