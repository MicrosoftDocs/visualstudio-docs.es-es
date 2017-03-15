---
title: "Error del compilador CS0656 | Microsoft Docs"
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
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0656
Falta el miembro necesario del compilador 'objeto.miembro'.  
  
 Existe uno de los siguientes problemas:  
  
-   La instalación de Common Language Runtime está dañada.  
  
-   Hay una referencia a un ensamblado que define un tipo que también se encuentra en Common Language Runtime. Sin embargo, el tipo del ensamblado no se define en la forma en que el compilador de C\# espera.  
  
 Compruebe las referencias para asegurarse de que usa la versión correcta de Common Language Runtime.