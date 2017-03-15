---
title: "Error del compilador CS1509 | Microsoft Docs"
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
  - "CS1509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1509"
ms.assetid: 51a475c3-f085-49cb-89b0-c6582b68653f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1509
El archivo 'archivo' al que se hace referencia no es un ensamblado; use la opción '\/addmodule' en su lugar.  
  
 Un archivo de salida \(archivo de salida 1\) producido en una compilación que usa [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) \(no tiene un manifiesto de ensamblado\), se especificó para [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option). Por lo tanto, en lugar de agregar un ensamblado al ensamblado para el programa actual, la información de metadatos del archivo de salida 1 se agregará al ensamblado para el programa actual.