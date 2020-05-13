---
title: Errores de depuración remota y solución de problemas de la herramienta de depuración remota ( Remote Debugging Errors and Troubleshooting) Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301072"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errores de la depuración remota y sus soluciones

Puede encontrarse con los siguientes errores al intentar depurar de forma remota.

- [Error: No se puede ir al servidor automáticamente](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Error: El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [No se puede conectar al Monitor de depuración remota de Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ejecute el depurador remoto como administrador

Puede encontrarse con problemas si no ejecuta el depurador remoto como administrador. Por ejemplo, puede ver el siguiente error: "El depurador remoto de Visual Studio (MSVSMON. EXE) tiene privilegios insuficientes para depurar este proceso." Si está ejecutando el depurador remoto como una aplicación (no como un servicio), es posible que vea el error de cuenta de [usuario diferente.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Al ejecutar el depurador remoto como un servicio

Al ejecutar el depurador remoto como servicio s, se recomienda ejecutarlo como administrador por varias razones:

- El servicio de depurador remoto solo permite conexiones de administradores, por lo que **no** se han introducido nuevos riesgos de seguridad ejecutándolo como administrador.

- Puede evitar errores que se producen cuando el usuario de Visual Studio tiene más derechos para depurar un proceso que el propio depurador remoto.

- Para simplificar la configuración del depurador remoto.

Aunque es posible depurar sin ejecutar el depurador remoto como administrador, hay varios requisitos para que esto funcione correctamente y a menudo requieren pasos de configuración de servicio más avanzados.

- La cuenta que está utilizando en el equipo remoto debe tener el inicio de **sesión como** privilegio de servicio. Consulte los pasos que se aparecen en "Para agregar inicio de sesión como servicio" en el artículo [No se puede volver a conectar](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) el error.

- La cuenta debe tener derechos para depurar el proceso de destino. Para obtener estos derechos, debe ejecutar el depurador remoto en la misma cuenta que el proceso que se va a depurar. (La alternativa más fácil es ejecutar el servicio como administrador.) 

- La cuenta debe poder conectarse de nuevo a (es decir, autenticarse con) el equipo de Visual Studio a través de la red. En un dominio, es más fácil conectarse de nuevo si el depurador remoto se ejecuta en las cuentas integradas de sistema local o servicio de red, o una cuenta de dominio. Las cuentas integradas tienen privilegios de seguridad elevados que pueden suponer un riesgo de seguridad.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Al ejecutar el depurador remoto como una aplicación (modo normal)

Si está intentando asociarse a su propio proceso no elevado (por ejemplo, una aplicación normal), no importa si está ejecutando el depurador remoto como administrador.

Desea ejecutar el depurador remoto como administrador en varios escenarios:

- Desea adjuntar a procesos que se ejecutan como otro usuario (por ejemplo, al depurar IIS) o

- Está intentando iniciar otro proceso y el proceso que desea iniciar es un administrador.

**No** desea ejecutar como administrador si desea iniciar procesos y el proceso que desea iniciar **no** debe ser un administrador.

## <a name="see-also"></a>Consulte también
- [Depuración remota](../debugger/remote-debugging.md)