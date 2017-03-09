---
title: "Error del compilador CS1667 | Microsoft Docs"
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
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1667
El atributo 'atributo' no es válido en descriptores de acceso de propiedad o evento. Solo es válido en declaraciones 'tipo de declaración'.  
  
 Este error se produce si se usa un atributo en un descriptor de acceso de propiedad o evento, cuando debería estar en la propiedad o el evento. Este error puede producirse con los atributos <xref:System.CLSCompliantAttribute>, <xref:System.Diagnostics.ConditionalAttribute> y <xref:System.ObsoleteAttribute>.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1670:  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```