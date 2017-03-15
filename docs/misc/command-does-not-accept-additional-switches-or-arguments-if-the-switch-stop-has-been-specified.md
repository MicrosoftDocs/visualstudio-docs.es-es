---
title: "Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified. | Microsoft Docs"
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
  - "vs.message.0x800A00CD"
  - "vs.message.VS_E_NOTVALIDWITHSTOP"
ms.assetid: 1dea2450-034e-4a7f-b959-2060811329b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified.
Este error ocurre normalmente cuando se especifica el modificador `/stop`, junto con modificadores adicionales para los comandos **Buscar en archivos** o **Reemplazar en archivos**.  
  
### Para corregir este error  
  
1.  Si desea detener la operación actual Buscar en archivos, escriba:  
  
    ```  
    Edit.FindinFiles /stop.  
    ```  
  
2.  Si desea detener la operación actual Reemplazar en archivos, escriba:  
  
    ```  
    Edit.ReplaceinFiles /stop  
    ```  
  
3.  Si desea iniciar una nueva operación Buscar\/Reemplazar en archivos, vuelva a escribir el comando omitiendo `/stop`.  
  
## Vea también  
 [Reemplazar en archivos \(Comando\)](../ide/reference/replace-in-files-command.md)   
 [Buscar en archivos \(Comando\)](../ide/reference/find-in-files-command.md)   
 [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)