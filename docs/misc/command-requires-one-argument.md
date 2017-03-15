---
title: "Command requires one argument. | Microsoft Docs"
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
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
Este error ocurre normalmente cuando no se especifica suficiente información sobre el comando o se utiliza una combinación incorrecta de argumentos.  
  
 Por ejemplo, si se escribe `alias` `/delete sample1 sample2` para el comando `alias`, aparece este error porque alias `/delete` sólo puede tomar un nombre de alias, no dos.  Los nombres de alias no contienen espacios, por lo que el cuadro **Buscar\/Comando** y la **Ventana de comandos** interpretan `sample1 sample2` como dos nombres de alias diferentes.  
  
### Para corregir este error  
  
1.  Compruebe cuál es la sintaxis correcta en la documentación del comando e inténtelo de nuevo.  
  
## Vea también  
 [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)