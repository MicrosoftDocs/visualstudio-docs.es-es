---
title: "Error del compilador CS1557 | Microsoft Docs"
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
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1557
No se puede usar 'class' para el método Main porque se encuentra en un archivo de salida diferente  
  
 La opción del compilador [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) se especificó para un archivo de salida en una compilación de varios archivos de salida. Sin embargo, no se encontró la clase en el código fuente de la compilación \/main; se encontró un archivo de código fuente de uno de los otros archivos de salida de la compilación.