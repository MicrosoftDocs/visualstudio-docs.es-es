---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfd6d9ac2493e4caca95538140fb9af78db8e074
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574313"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [-Log (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/log-devenv-exe).  
  
  
Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De manera predeterminada, el archivo de registro es:  
  
 *% APPDATA %* \Microsoft\VisualStudio\\*Versión*\ActivityLog.xml  
  
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



