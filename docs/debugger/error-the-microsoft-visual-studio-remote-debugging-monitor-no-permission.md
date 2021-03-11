---
description: Este error aparece cuando el usuario que intenta ejecutar el Monitor de depuración remota de Visual Studio (msvsmon) no tiene una cuenta en el equipo local.
title: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse con este equipo
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f35db1d84d0f44eedbc8bf09f1e5ff9a6f49e5f2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146736"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse con este equipo

Este error aparece cuando el usuario que intenta ejecutar el Monitor de depuración remota de Visual Studio (msvsmon) no tiene una cuenta en el equipo local. Este error puede producirse cuando se realiza la depuración remota con el motor de depuración heredado.

## <a name="to-fix-this-problem"></a>Para corregir este problema

- Agregue una cuenta de usuario al equipo host del depurador de Visual Studio, con el mismo nombre y contraseña que la cuenta de usuario que ejecuta msvsmon en el equipo remoto

   \- o -

- Ejecute msvsmon como un usuario que tiene permiso para llamar en el equipo local. Esto indica que el usuario debe ser un usuario de dominio y administrador en el equipo de msvsmon. Puede especificar la cuenta de usuario para ejecutar msvsmon de dos maneras:

  - Haga clic con el botón derecho en el icono de msvsmon y elija **Ejecutar como** en el menú contextual

    \- o -

  - En el símbolo del sistema, ejecute `runas.exe`.

## <a name="see-also"></a>Vea también

- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
