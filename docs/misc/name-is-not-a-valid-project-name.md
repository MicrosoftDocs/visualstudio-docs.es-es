---
title: "&lt;name&gt; is not a valid project name. | Microsoft Docs"
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
  - "vs.message.VS_E_INVALIDPROJECTNAME"
  - "vs.message.0x800A00D2"
ms.assetid: 2e8f3e58-f5f0-4f12-bae9-3acc58c0dca6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid project name.
Este error se produce normalmente cuando se ejecuta el comando `File.NewProject` desde la ventana **Comando** o el cuadro **Buscar\/Comando** y se escribe un nombre de proyecto incorrecto para *projectname*.  
  
### Para corregir este error  
  
1.  Compruebe que el nombre de proyecto no contiene espacios extra y no es una palabra reservada como NUL, CON o AUX.  
  
     \-O bien\-  
  
     Vuelva a escribir el comando, omitiendo el nombre de proyecto.  
  
## Vea también  
 [Ventana de comandos](../ide/reference/command-window.md)