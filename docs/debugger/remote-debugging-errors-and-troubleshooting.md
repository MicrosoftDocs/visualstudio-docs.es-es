---
title: Errores de la depuración remota y sus soluciones | Microsoft Docs
description: Consulte los vínculos a los errores habituales de depuración remota en Visual Studio. Obtenga información sobre cómo ejecutar el depurador remoto como administrador.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0260f939c8f6b7e5bed77ec42a4720adf0a4c720
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205663"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errores de la depuración remota y sus soluciones

Al intentar depurar remotamente se pueden producir los siguientes errores.

- [Error: No se puede depurar paso a paso por instrucciones al servidor de manera automática](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Error: El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Error: La máquina remota no aparece en el cuadro de diálogo Conexiones remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ejecutar el depurador remoto como administrador

Puede que surjan problemas si no ejecuta el depurador remoto como administrador. Por ejemplo, puede ver el siguiente error: "Visual Studio Remote Debugger (MSVSMON.EXE) tiene privilegios insuficientes para depurar este proceso. " Si ejecuta el depurador remoto como aplicación (y no como servicio), es posible que vea el error de [cuenta de usuario diferente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md).

### <a name="when-running-the-remote-debugger-as-a-service"></a>Al ejecutar el depurador remoto como servicio

Al ejecutar el depurador remoto como servicio, se recomienda ejecutarlo como administrador por varias razones:

- El servicio del depurador remoto solo permite conexiones de administradores, por lo que **no** hay nuevos riesgos de seguridad introducidos al ejecutarlo como administrador.

- Puede impedir que se produzcan errores cuando el usuario de Visual Studio tiene más derechos para depurar un proceso que el propio depurador remoto.

- Para simplificar la instalación y configuración del depurador remoto.

Aunque es posible depurar sin ejecutar el depurador remoto como administrador, hay varios requisitos para que funcione correctamente y, a menudo, requieren pasos de configuración de servicio más avanzados.

- La cuenta que usa en el equipo remoto debe tener el privilegio **Iniciar sesión como servicio**. Consulte los pasos descritos en "Para agregar un inicio de sesión como servicio" en el artículo sobre el error [No se puede volver a conectar](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

- La cuenta debe tener derechos para depurar el proceso de destino. Para obtener estos derechos, debe ejecutar el depurador remoto en la misma cuenta que el proceso que se va a depurar (la alternativa más sencilla consiste en ejecutar el servicio como administrador). 

- La cuenta debe poder conectarse de nuevo (es decir, autenticarse) al equipo de Visual Studio a través de la red. En un dominio es más fácil volver a conectarse si el depurador remoto se ejecuta en las cuentas de sistema local o de servicio de red integradas, o bien en una cuenta de dominio. Las cuentas integradas tienen privilegios de seguridad elevados que pueden suponer un riesgo para la seguridad.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Al ejecutar el depurador remoto como aplicación (modo normal)

Si intenta asociarlo a su propio proceso sin privilegios elevados (por ejemplo, una aplicación normal), no importa si ejecuta el depurador remoto como administrador.

Desea ejecutar el depurador remoto como administrador en varios escenarios:

- Desea asociarlo a procesos que se ejecutan como otro usuario (por ejemplo, al depurar IIS); o

- intenta iniciar otro proceso y este es un administrador.

**No** desea ejecutarlo como administrador si desea iniciar procesos, y este **no** debe ser un administrador.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)