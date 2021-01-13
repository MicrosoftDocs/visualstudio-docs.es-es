---
title: Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso.
titleSuffix: ''
description: "\"Error DCOM inesperado al intentar ponerse en contacto con el equipo remoto. Acceso denegado\". Obtenga información sobre esta referencia de error de depuración remota de Visual Studio."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c430462a224cb4604c09984a5397e540ce752b8a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729202"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso.
La depuración remota utiliza DCOM para la comunicación entre el host y los equipos remotos en las siguientes situaciones:

- El depurador está establecido en el **Modo de compatibilidad nativa** o el **Modo de compatibilidad administrado** está activado en la página **Herramientas / Opciones / Depuración**.

- Está depurando código C++ (C++ / CLI) administrado.

- En Visual Studio 2013, cuando se activa **Habilitar la opción Editar y continuar nativa** en la página **Herramientas / Opciones / Depuración**.

- Algunos escenarios de depuración de terceros

  Este error se produce cuando el proceso de Visual Studio no puede autenticarse (o las credenciales proporcionadas se consideran insuficientes) al proceso del depurador remoto sobre DCOM. Una o varias de las siguientes soluciones podrían resolver el problema:

- Desactive el  **Modo de compatibilidad nativa** y el **Modo de compatibilidad administrado**.

- En Visual Studio 2013, desactive **Habilitar la opción Editar y continuar nativa**.

- Reinicie ambos equipos.

- Si la depuración remota requiere proporcionar las credenciales, active la opción para guardar las credenciales.

## <a name="see-also"></a>Vea también

- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)