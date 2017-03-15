---
title: "Error del compilador CS0415 | Microsoft Docs"
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
  - "CS0415"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0415"
ms.assetid: 1ed45b02-4568-4af4-b2a6-c8b01230d19a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0415
El atributo 'IndexerName' solo es válido en un indexador que no sea una declaración de miembro de interfaz explícita  
  
 Este error se produce si se utiliza un atributo IndexerName en un indexador que es una implementación explícita de una interfaz. Este error se puede evitar quitando el nombre de interfaz de la declaración del indexador, si es posible. Para más información, consulte [Clase IndexerNameAttribute](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic).  
  
 El ejemplo siguiente genera la advertencia CS0415:  
  
```  
// CS0415.cs using System; using System.Runtime.CompilerServices; public interface IA { int this[int index] { get; set; } } public class A : IA { [IndexerName("Item")]  // CS0415 int IA.this[int index] // Try this line instead: // public int this[int index] { get { return 0; } set { } } static void Main() { } }  
```