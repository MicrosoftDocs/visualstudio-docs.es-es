---
title: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03e4ef05c1615e7798cd111f9cc5f95976abeebc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871330"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto
Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:

 El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto.

## <a name="cause"></a>Motivo
 Este mensaje aparece cuando se lleva a cabo la depuración en modo Sin autenticación y el usuario que inició msvsmon no es el usuario que ejecuta Visual Studio.

## <a name="solution"></a>Soluciones
 La solución mejor y más segura es ejecutar el Monitor de depuración remota (msvsmon.exe) con la misma cuenta de usuario que Visual Studio. Si no es posible hacerlo, puede ejecutar el Monitor de depuración remota con otra cuenta activando la opción **Permitir que cualquier usuario depure** en el cuadro de diálogo **Opciones** del Monitor de depuración remota.

> [!CAUTION]
> Si se concede permiso a otros usuarios para que se conecten, existe la posibilidad de que se conecten accidentalmente a la sesión de depuración remota equivocada. Llevar a cabo la depuración en modo **Sin autenticación** no es seguro y debe utilizarse con precaución.

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)