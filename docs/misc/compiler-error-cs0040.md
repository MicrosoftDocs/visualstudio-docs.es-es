---
title: "Error del compilador CS0040 | Microsoft Docs"
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
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0040
Error inesperado al crear el archivo de información de depuración: 'reason'  
  
 Este error puede producirse al usar la opción del compilador [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) e indica que el compilador no pudo escribir en el archivo .pdb. Entre las posibles soluciones a este error se incluyen reinstalar Visual Studio, asegurando que el compilador tenga acceso de escritura en un archivo o directorio, o no compilar con\/debug.