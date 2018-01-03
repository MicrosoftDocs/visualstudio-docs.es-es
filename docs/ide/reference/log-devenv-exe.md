---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb84c4bab7ce9480deefbb88ac02289415f33d5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De manera predeterminada, el archivo de registro es:  
  
 *% APPDATA %*\Microsoft\VisualStudio\\*Versión*\ActivityLog.xml  
  
 en que *Versión* es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.  
  
 El registro se escribe para todas las instancias de Visual Studio que se han invocado con el modificador /log. No registra las instancias de Visual Studio que se han invocado sin el modificador.  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)