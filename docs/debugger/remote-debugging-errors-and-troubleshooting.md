---
title: Errores y solución de problemas de depuración remota | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187520"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errores de la depuración remota y sus soluciones

Puede que se produzcan los siguientes errores al intentar depurar de forma remota.

- [Error: Unable to Automatically Step Into the Server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Error: Parece que el Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no se está ejecutando en el equipo remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ejecutar el depurador remoto como administrador

Puede que surjan problemas si no ejecuta el depurador remoto como administrador. Por ejemplo, puede ver el siguiente error: "The Visual Studio Remote Debugger (MSVSMON. EXE) no tiene privilegios suficientes para depurar este proceso. " Si ejecuta el depurador remoto como una aplicación (no un servicio), es posible que vea el error de [cuenta de usuario diferente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Al ejecutar el depurador remoto como servicio

Al ejecutar el depurador remoto como servicio de, se recomienda ejecutarlo como administrador por varias razones:

- El servicio del Depurador remoto solo permite conexiones de los administradores, por lo que no hay **ningún** riesgo de seguridad nuevo al ejecutarlo como administrador.

- Puede impedir que se produzcan errores cuando el usuario de Visual Studio tiene más derechos para depurar un proceso que el propio Depurador remoto.

- Para simplificar la instalación y configuración del Depurador remoto.

Aunque es posible depurar sin ejecutar el depurador remoto como administrador, hay varios requisitos para que funcione correctamente y, a menudo, requieren pasos de configuración de servicio más avanzados.

- La cuenta que está usando en el equipo remoto debe tener el privilegio **iniciar sesión como servicio** . Consulte los pasos descritos en "para agregar inicio de sesión como servicio" en el artículo [no se puede volver a conectar](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) el error.

- La cuenta debe tener derechos para depurar el proceso de destino. Para obtener estos derechos, debe ejecutar el depurador remoto en la misma cuenta que el proceso que se va a depurar. (La alternativa más sencilla es ejecutar el servicio como administrador). 

- La cuenta debe poder conectarse de nuevo a (es decir, autenticarse con) el equipo de Visual Studio a través de la red. En un dominio, es más fácil volver a conectarse si el depurador remoto se ejecuta en las cuentas de sistema local o de servicio de red integradas, o en una cuenta de dominio. Las cuentas integradas tienen privilegios de seguridad elevados que pueden suponer un riesgo para la seguridad.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Al ejecutar el depurador remoto como una aplicación (modo normal)

Si intenta asociar a su propio proceso sin privilegios elevados (como una aplicación normal), no importa si ejecuta el depurador remoto como administrador.

Desea ejecutar el depurador remoto como administrador en varios escenarios:

- Desea asociar a procesos que se ejecutan como otro usuario (por ejemplo, al depurar IIS) o

- Está intentando iniciar otro proceso y el proceso que desea iniciar es un administrador.

**No desea ejecutar** como administrador si desea iniciar procesos, y el proceso que desea iniciar **no** debe ser un administrador de.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)