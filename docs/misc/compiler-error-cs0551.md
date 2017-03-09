---
title: "Error del compilador CS0551 | Microsoft Docs"
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
  - "CS0551"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0551"
ms.assetid: fb456ecf-dff3-4e39-b9b3-de23d81dadea
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0551
A la implementación de interfaz explícita 'implementación' le falta el descriptor de acceso 'descriptor de acceso'.  
  
 Una clase que implementa explícitamente la propiedad de la interfaz debe implementar todos los descriptores de acceso que define la interfaz.  
  
 Para obtener más información, consulta [Utilizar propiedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0551.  
  
```  
// CS0551.cs // compile with: /target:library interface ii { int i { get; set; } } public class a : ii { int ii.i { set {} }   // CS0551 // OK int ii.i { set {} get { return 0; } } }  
```