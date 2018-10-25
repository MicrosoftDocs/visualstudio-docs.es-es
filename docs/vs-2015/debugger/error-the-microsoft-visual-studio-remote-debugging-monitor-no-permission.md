---
title: 'Error: El Microsoft Visual Studio Monitor de depuración remota en el equipo remoto no tiene permiso para conectarse a este equipo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20accedd9591c777cad26aed30c05954dfabbdfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811094"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse a este equipo.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error aparece cuando el usuario que intenta ejecutar el Monitor de depuración remota de Visual Studio (msvsmon) no tiene una cuenta en el equipo local.  
  
### <a name="to-fix-this-problem"></a>Para corregir este problema  
  
- Agregue una cuenta de usuario al equipo host del depurador de Visual Studio, con el mismo nombre y contraseña que la cuenta de usuario que ejecuta msvsmon en el equipo remoto  
  
   \- o -  
  
- Ejecute msvsmon como un usuario que tiene permiso para llamar en el equipo local. Esto indica que el usuario debe ser un usuario de dominio y administrador en el equipo de msvsmon. Puede especificar la cuenta de usuario para ejecutar msvsmon de dos maneras:  
  
  - Haga clic en el icono de msvsmon y elija **ejecución** en el menú contextual  
  
    \- o -  
  
  - En el símbolo del sistema, ejecute `runas.exe`.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota en dominios](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



