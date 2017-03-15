---
title: "Error del compilador CS0273 | Microsoft Docs"
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
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0273
El modificador de accesibilidad del descriptor de acceso 'property\_accessor' debe ser más restrictivo que la propiedad o el indexador 'property'  
  
 El modificador de accesibilidad del descriptor de acceso set\/get debe ser más restrictivo que la propiedad o el indexador 'property\/indexer'  
  
 Este error se produce cuando se declara una propiedad o un indexador con un modificador de acceso que es menos restrictivo que el modificador de acceso en uno de sus descriptores de acceso. Para resolver este error, use el modificador de acceso apropiado en la propiedad o el descriptor de acceso set. Para más información, vea [Accesibilidad del descriptor de acceso](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Ejemplo  
 Este ejemplo contiene una propiedad internal con un método internal set. El ejemplo siguiente genera la advertencia CS0273.  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```