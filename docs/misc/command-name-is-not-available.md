---
title: "Command &lt;name&gt; is not available. | Microsoft Docs"
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
  - "vs.message.VS_E_DISABLEDCOMMAND"
  - "vs.message.0x800A00A6"
ms.assetid: 22d6033f-e00a-4479-9a62-025dd781ed34
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command &lt;name&gt; is not available.
Este error se produce normalmente cuando se escribe un comando en la ventana **Comando** o en el cuadro **Buscar\/Comando** que no es válido con respecto al estado actual de Visual Studio.  Por ejemplo, el comando `File.CloseSolution`  no es válido si hay una solución abierta en esos momentos en Visual Studio.  
  
### Para corregir este error  
  
1.  Elija un comando diferente.  
  
     \-O bien\-  
  
     Realice una selección diferente para ejecutar el comando.  
  
## Vea también  
 [Ventana de comandos](../ide/reference/command-window.md)