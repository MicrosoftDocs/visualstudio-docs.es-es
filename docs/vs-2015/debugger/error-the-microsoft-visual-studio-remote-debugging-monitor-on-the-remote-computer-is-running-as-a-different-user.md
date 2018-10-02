---
title: 'Error: El Microsoft Visual Studio Monitor de depuración remota en el equipo remoto se está ejecutando como otro usuario | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5256feb22e09eb75fa8f4d5a50e8beafeec8f97d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577518"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando con un usuario diferente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: The Microsoft Visual Studio Monitor de depuración remota en el equipo remoto se está ejecutando como otro usuario](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user).  
  
Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
 El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto.  
  
## <a name="cause"></a>Motivo  
 Este mensaje aparece cuando se lleva a cabo la depuración en modo Sin autenticación y el usuario que inició msvsmon no es el usuario que ejecuta Visual Studio.  
  
## <a name="solution"></a>Soluciones  
 La solución mejor y más segura es ejecutar el Monitor de depuración remota (msvsmon.exe) con la misma cuenta de usuario que Visual Studio. Si no puede hacer eso, puede ejecutar el Monitor de depuración remota con otra cuenta con la **permitir que cualquier usuario depure** opción seleccionada en el Monitor de depuración remota **opciones** cuadro de diálogo.  
  
> [!CAUTION]
>  Si se concede permiso a otros usuarios para que se conecten, existe la posibilidad de que se conecten accidentalmente a la sesión de depuración remota equivocada. Depuración en **sin autenticación** modo no es seguro y debe utilizarse con precaución.  
  
 Para obtener más información, consulte [iniciar el Monitor de depuración remota](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)



