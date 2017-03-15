---
title: "Error del compilador CS1617 | Microsoft Docs"
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
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1617
Opción 'option' no válida para \/langversion; debe ser ISO\-2, ISO\-2, 3, 4, 5 o Default.  
  
 Este error se produce si usó la configuración de proyecto o el modificador de la línea de comandos [\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) pero no especificó una opción de lenguaje válida. Para resolver este error, compruebe la sintaxis de línea de comandos o la configuración de proyecto, y cambie a una de las opciones enumeradas.  
  
 Por ejemplo, al compilar con `csc /langversion:ISO` se generará el error CS1617.