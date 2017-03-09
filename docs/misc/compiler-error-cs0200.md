---
title: "Error del compilador CS0200 | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0200
No se puede asignar la propiedad o el indexador 'property' \(es de solo lectura\)  
  
 Se intentó asignar un valor a [property](/dotnet/csharp/programming-guide/classes-and-structs/using-properties), pero la propiedad no tiene un descriptor de acceso set. Para resolver el error agregue un descriptor de acceso set. Para obtener más información, consulta [Cómo: Declarar y usar propiedades de lectura y escritura](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0200:  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```