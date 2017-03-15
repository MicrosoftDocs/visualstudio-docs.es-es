---
title: "Error del compilador de recursos RC2115 | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Error del compilador de recursos RC2115
Se esperaba una cadena de texto o un ordinal en el control  
  
 El campo *text* de una instrucción de CONTROL en la instrucción **DIALOG** debe ser una cadena de texto o una referencia ordinal al tipo de control. Si usa un ordinal, asegúrese de que tiene una instrucción `#define` para el control.