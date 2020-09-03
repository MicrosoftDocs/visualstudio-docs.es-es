---
title: Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156531"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración remota utiliza DCOM para la comunicación entre el host y los equipos remotos en las siguientes situaciones:  
  
- El depurador está establecido en **modo de compatibilidad nativo** o el **modo de compatibilidad administrado** está activado en la página **herramientas/opciones/depuración**  
  
- Está depurando código C++ (C++ / CLI) administrado.  
  
- En Visual Studio 2013, cuando se activa habilitar la opción **Editar y continuar nativa** en la página **herramientas/opciones/depuración**  
  
- Algunos escenarios de depuración de terceros  
  
  Este error se produce cuando el proceso de Visual Studio no puede autenticarse (o las credenciales proporcionadas se consideran insuficientes) al proceso del depurador remoto sobre DCOM. Una o varias de las siguientes soluciones podrían resolver el problema:  
  
- Desactive el  **Modo de compatibilidad nativa** y el **Modo de compatibilidad administrado**.  
  
- En Visual Studio 2013, desactive **Habilitar la opción Editar y continuar nativa**.  
  
- Reinicie ambos equipos.  
  
- Si la depuración remota requiere proporcionar las credenciales, active la opción para guardar las credenciales.  
  
## <a name="see-also"></a>Consulte también  
 [Errores y solución de problemas de depuración remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
