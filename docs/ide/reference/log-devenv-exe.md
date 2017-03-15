---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log (modificador para Devenv)"
  - "Devenv, /Log (modificador)"
  - "Log (modificador) [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Registra toda la actividad en el archivo de registro para solucionar problemas.  Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez.  De manera predeterminada, el archivo de registro es:  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Versión*\\ActivityLog.xml  
  
 Aquí, *Versión* es la versión de Visual Studio.  Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.  
  
## Sintaxis  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## Comentarios  
 Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.  
  
 El registro se escribe para todas las instancias de Visual Studio que se han invocado con el modificador \/log.  No registra las instancias de Visual Studio que se han invocado sin el modificador.  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)