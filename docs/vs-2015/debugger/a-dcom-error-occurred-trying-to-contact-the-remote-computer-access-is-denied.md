---
title: Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso. | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cabac4997480b626714c129daef0511643ae2a50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580510"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Error DCOM al intentar ponerse en contacto con el equipo remoto. Se denegó el acceso.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DCOM de un error al intentar ponerse en contacto con el equipo remoto. Acceso denegado. ](https://docs.microsoft.com/visualstudio/debugger/a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied).  
  
La depuración remota utiliza DCOM para la comunicación entre el host y los equipos remotos en las siguientes situaciones:  
  
-   El depurador está establecido en el **Modo de compatibilidad nativa** o el **Modo de compatibilidad administrado** está activado en la página **Herramientas / Opciones / Depuración**   
  
-   Está depurando código C++ (C++ / CLI) administrado.  
  
-   En Visual Studio 2013, cuando se activa **Habilitar la opción Editar y continuar nativa** en la página **Herramientas / Opciones / Depuración**  
  
-   Algunos escenarios de depuración de terceros  
  
 Este error se produce cuando el proceso de Visual Studio no puede autenticarse (o las credenciales proporcionadas se consideran insuficientes) al proceso del depurador remoto sobre DCOM. Una o varias de las siguientes soluciones podrían resolver el problema:  
  
-   Desactive el  **Modo de compatibilidad nativa** y el **Modo de compatibilidad administrado**.  
  
-   En Visual Studio 2013, desactive **Habilitar la opción Editar y continuar nativa**.  
  
-   Reinicie ambos equipos.  
  
-   Si la depuración remota requiere proporcionar las credenciales, active la opción para guardar las credenciales.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)



