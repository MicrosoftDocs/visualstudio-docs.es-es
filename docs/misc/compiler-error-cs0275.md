---
title: "Error del compilador CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0275
'accessor': no se pueden usar modificadores de accesibilidad en descriptores de acceso de una interfaz  
  
 Este error se produce cuando se usa un modificador de acceso en cualquiera de los descriptores de acceso de una propiedad o indexador en una interfaz. Para resolverlo, quite el modificador de acceso.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0275:  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```