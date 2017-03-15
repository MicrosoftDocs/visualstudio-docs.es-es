---
title: "Error del compilador CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1541
Opción de referencia no válida: 'symbol': no puede hacer referencia a directorios  
  
 El compilador detectó un intento de especificar un directorio en lugar de un archivo específico. Por ejemplo, cuando use la opción del compilador [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option), debe especificar un archivo; no es posible especificar un directorio.  
  
 Por ejemplo, si se pasa `/reference:c:\` al compilador generará el error CS1541.