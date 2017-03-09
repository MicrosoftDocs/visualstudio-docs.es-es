---
title: "Error del compilador CS1562 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1562
Los resultados sin origen deben tener la opción \/out especificada  
  
 La compilación pudo crear un archivo de salida, pero no había ningún archivo de código fuente como entrada desde el que se pudiera deducir el nombre del archivo de salida. Por ejemplo, es posible que intente compilar un archivo de solo metadatos o de solo de recursos.  
  
 Use la opción del compilador [\/Fd](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) para especificar el nombre del archivo de salida.