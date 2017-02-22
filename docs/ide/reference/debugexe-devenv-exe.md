---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/DebugExe [devenv.exe]"
  - "DebugExe (modificador)"
  - "Devenv, /DebugExe (modificador)"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre el archivo ejecutable especificado que se va a depurar.  
  
## Sintaxis  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## Argumentos  
 `ExecutableFile`  
 Obligatorio.  Ruta de acceso y nombre de un archivo .exe.  
  
 Si no se encuentra el archivo .exe o no existe, no se muestra ninguna advertencia o error y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicia normalmente.  
  
## Comentarios  
 Cualquier cadena que siga al parámetro `ExecutableFile` se pasa a dicho archivo como argumentos.  
  
## Ejemplo  
 En el siguiente ejemplo, se abre el archivo `MyApplication.exe` para su depuración.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)