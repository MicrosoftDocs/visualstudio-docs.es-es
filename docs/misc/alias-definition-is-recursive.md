---
title: "Alias definition is recursive. | Microsoft Docs"
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
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
Este error ocurre normalmente cuando se ha definido un alias que hace referencia directa o indirecta a sí mismo.  
  
### Para corregir este error  
  
1.  Cambie la definición del alias e inténtelo de nuevo.  
  
     \-O bien\-  
  
2.  Revise la lista actual de alias y sus definiciones escribiendo `>alias` en la **Ventana de comandos** e inténtelo de nuevo.  
  
## Vea también  
 [Alias \(Comando\)](../ide/reference/alias-command.md)   
 [Alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md)