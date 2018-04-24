---
title: 'Error: El Microsoft Visual Studio Monitor de depuración remota en el equipo remoto está ejecutando como otro usuario | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2bdc731b65a8d451b6882914e8bed1abca2139b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando con un usuario diferente
Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
 El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto.  
  
## <a name="cause"></a>Motivo  
 Este mensaje aparece cuando se lleva a cabo la depuración en modo Sin autenticación y el usuario que inició msvsmon no es el usuario que ejecuta Visual Studio.  
  
## <a name="solution"></a>Soluciones  
 La solución mejor y más segura es ejecutar el Monitor de depuración remota (msvsmon.exe) con la misma cuenta de usuario que Visual Studio. Si no es posible hacerlo, puede ejecutar el Monitor de depuración remota con otra cuenta con la **permitir que cualquier usuario depure** opción seleccionada en el Monitor de depuración remota **opciones** cuadro de diálogo.  
  
> [!CAUTION]
>  Si se concede permiso a otros usuarios para que se conecten, existe la posibilidad de que se conecten accidentalmente a la sesión de depuración remota equivocada. Depuración en **sin autenticación** modo no es seguro y debe utilizarse con precaución.
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)