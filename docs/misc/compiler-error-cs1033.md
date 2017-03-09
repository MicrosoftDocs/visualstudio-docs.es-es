---
title: "Error del compilador CS1033 | Microsoft Docs"
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
  - "CS1033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1033"
ms.assetid: eb0f4001-84a6-4918-a648-cf710d038de7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1033
El archivo de origen ha superado el límite de 16.707.565 líneas representables en el PDB. La información de depuración no será correcta  
  
 Un archivo de código fuente superó el número máximo permitido de líneas que el compilador puede procesar. Para resolver este error, cree dos o más archivos de código fuente a partir del archivo original. El número máximo de líneas es 268 435 454. Si está usando **\/debug** y usa más de 16 707 566, se generará información de depuración dañada.