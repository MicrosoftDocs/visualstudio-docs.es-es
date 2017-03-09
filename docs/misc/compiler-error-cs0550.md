---
title: "Error del compilador CS0550 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0550"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0550"
ms.assetid: 57278c17-443c-40f2-9ebd-853558743564
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0550
'descriptor de acceso' agrega un descriptor de acceso que no se encuentra en el miembro de interfaz 'propiedad'.  
  
 La implementación de una propiedad en una clase derivada contiene un descriptor de acceso que no se especificó en la interfaz base.  
  
 Para obtener más información, consulta [Utilizar propiedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0550.  
  
```  
// CS0550.cs namespace x { interface ii { int i { get; // add the following accessor to resolve this CS0550 // set; } } public class a : ii { int ii.i { get { return 0; } set {}   // CS0550  no set in interface } public static void Main() {} } }  
```