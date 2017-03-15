---
title: "Error del compilador CS0274 | Microsoft Docs"
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
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0274
No se pueden especificar modificadores de accesibilidad para ambos descriptores de acceso de la propiedad o el indexador 'property\/indexer'  
  
 Este error se produce cuando se declara una propiedad o un indexador con modificadores de acceso en ambos descriptores de acceso. Para resolver este error, use un modificador de acceso solo en uno de los dos descriptores de acceso. Para más información, vea [Accesibilidad del descriptor de acceso](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
 En el siguiente ejemplo se genera el error CS0274:  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```