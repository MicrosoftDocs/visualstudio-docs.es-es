---
description: Este error significa que el servicio del depurador remoto se ejecuta con una cuenta de usuario que no se puede autenticar cuando intenta conectarse al equipo desde el que se realiza la depuración.
title: El servicio Visual Studio Remote Debugger del equipo de destino no se puede conectar a este equipo
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a08f1a7638233e2633a34287aad500ee81245be6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146696"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Error: El servicio Visual Studio Remote Debugger del equipo de destino no se puede conectar a este equipo
Este error significa que el servicio del depurador remoto se ejecuta con una cuenta de usuario que no se puede autenticar cuando intenta conectarse al equipo desde el que se realiza la depuración. Este error se puede producir cuando se realiza la depuración remota con el motor de depuración heredado y el depurador remoto se ejecuta como un servicio.

 En la tabla siguiente se muestran las cuentas que pueden tener acceso al equipo:

|Escenario|Cuenta LocalSystem|Cuenta de dominio|Cuentas locales con el mismo nombre de usuario y contraseña en ambos equipos|
|-|-|-|-|
|Ambos equipos en el mismo dominio|Sí|Sí|Sí|
|Ambos equipos en dominios que tienen confianza bidireccional|No|No|Sí|
|Uno o ambos equipos en un grupo de trabajo|No|No|Sí|
|Equipos en dominios diferentes|No|No|Sí|

 Además:

- La cuenta en la que se ejecuta el servicio del depurador remoto de Visual Studio debe ser una cuenta de administrador en el equipo remoto, de modo que éste pueda depurar cualquier proceso.

- La cuenta también necesita tener el privilegio `Log on as a service` en el equipo remoto que usa la herramienta administrativa **Directiva de seguridad local**.

- Si está usando un acceso de cuenta local al equipo, debe ejecutar el servicio del depurador remoto de Visual Studio con una cuenta local.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Asegúrese de que el servicio del depurador remoto de Visual Studio esté correctamente configurado en el equipo remoto. Para obtener más información, vea [Depuración remota](../debugger/remote-debugging.md).

2. Ejecute el servicio del depurador remoto bajo una cuenta que puede tener acceso al equipo host del depurador, como se muestra en la tabla anterior.

### <a name="to-add-log-on-as-a-service-privilege"></a>Para agregar el privilegio "Iniciar sesión como servicio"

1. En el menú **Inicio**, elija **Panel de control**.

2. En Panel de control, elija **Vista clásica** si es necesario.

3. Haga doble clic en **Herramientas administrativas**.

4. En la ventana Herramientas administrativas, haga doble clic en **Directiva de seguridad local**.

5. En la ventana **Configuración de seguridad local**, expanda la carpeta **Directivas locales**.

6. Haga clic en **Asignación de derechos de usuario**.

7. En la columna **Directiva**, haga doble clic en **Iniciar sesión como servicio** para ver las asignaciones de directiva de grupo local en el cuadro de diálogo **Iniciar sesión como servicio**.

8. Para agregar nuevos usuarios, haga clic en el botón **Agregar usuario o grupo**.

9. Cuando haya terminado de agregar usuarios, haga clic en **Aceptar**.

### <a name="to-work-around-this-error"></a>Para solucionar este error

- Ejecute el Monitor de depuración remota como aplicación en lugar de como servicio.

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
