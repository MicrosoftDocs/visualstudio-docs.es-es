---
title: Errores de depuración remota y sus soluciones | Documentos de Microsoft
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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043345"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errores de la depuración remota y sus soluciones

Puede encontrarse los siguientes errores al intentar depurar de forma remota.

- [Error: No se puede depurar paso a paso por instrucciones al servidor de manera automática](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Error: El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Error: La máquina remota no aparece en el cuadro de diálogo Conexiones remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ejecutar al depurador remoto como administrador

Puede encontrarse problemas si no ejecuta al depurador remoto como administrador. Por ejemplo, puede ver el error siguiente: "El Visual Studio Remote Debugger (MSVSMON. (EXE) tiene privilegios suficientes para depurar este proceso." Si se ejecuta el depurador remoto como una aplicación (no es un servicio), es posible que vea el [otra cuenta de usuario](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) error.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Cuando se ejecuta al depurador remoto como un servicio

Cuando se ejecuta al depurador remoto como servicio s, se recomienda ejecutarlo como administrador por varias razones:

- El servicio del depurador remoto solo permite conexiones a los administradores, por lo que hay **ningún** nuevos riesgos de seguridad introducidos por ejecutarlo como administrador.

- Puede evitar errores que realiza el resultado cuando el usuario de Visual Studio tiene más derechos para depurar un proceso que el propio depurador remoto.

- Para simplificar la instalación y configuración del depurador remoto.

Aunque es posible depurar sin ejecutar al depurador remoto como administrador, hay varios requisitos para llevarlo a cabo correctamente y a menudo requieren pasos de configuración de servicio más avanzados.

- La cuenta que está usando en el equipo remoto debe tener la **iniciar sesión como servicio** con privilegios. Consulte los pasos descritos en "Para agregar inicio de sesión como servicio" en el [no se puede conectar nuevo](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) artículo del error.

- La cuenta debe tener derechos para depurar el proceso de destino. Para obtener estos derechos, debe ejecutar al depurador remoto en la misma cuenta que el proceso que se desea depurar. (La alternativa más sencilla es ejecutar el servicio como un administrador). 

- La cuenta debe ser capaz de conectarse a volver a (es decir, se autentican con) el equipo de Visual Studio a través de la red. En un dominio, es más fácil conectarse si el depurador remoto se ejecuta en las cuentas Local System o Network Service integradas, o una cuenta de dominio. Las cuentas integradas tienen privilegios de seguridad que pueden presentar un riesgo de seguridad elevados.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Cuando se ejecuta al depurador remoto como una aplicación (modo normal)

Si está intentando conectar a su propio proceso sin privilegios elevados (por ejemplo, una aplicación normal), no importa si está ejecutando al depurador remoto como administrador.

Desea ejecutar al depurador remoto como administrador en varios escenarios:

- Que desea asociar a procesos que se ejecuta como otro usuario (por ejemplo, cuando la depuración de IIS), o

- Está intentando iniciar otro proceso y el proceso que desea iniciar es un administrador.

De lo **no** desea ejecutar como administrador si desea iniciar los procesos, y el proceso que desea iniciar debe **no** ser un administrador.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)