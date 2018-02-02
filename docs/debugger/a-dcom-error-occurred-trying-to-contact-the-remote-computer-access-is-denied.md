---
title: "Se ha producido un error DCOM intentar ponerse en contacto con el equipo remoto. Se denegó el acceso. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a861d3af9ae02fbbfc4fac2b38cc76058c8a3caf
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Se ha producido un error DCOM intentar ponerse en contacto con el equipo remoto. Se denegó el acceso.
La depuración remota utiliza DCOM para la comunicación entre el host y los equipos remotos en las siguientes situaciones:  
  
-   El depurador está configurado para **modo de compatibilidad nativa** o **modo de compatibilidad administrado** está activada en la **Herramientas > Opciones > depuración** página  
  
-   Está depurando código C++ (C++ / CLI) administrado.  
  
-   En Visual Studio 2013, cuando **habilitar nativo editar y continuar** está activada en la **Herramientas > Opciones > depuración** página  
  
-   Algunos escenarios de depuración de terceros  
  
 Este error se produce cuando el proceso de Visual Studio no puede autenticarse (o las credenciales proporcionadas se consideran insuficientes) al proceso del depurador remoto sobre DCOM. Una o varias de las siguientes soluciones podrían resolver el problema:  
  
-   Desactive el  **Modo de compatibilidad nativa** y el **Modo de compatibilidad administrado**.  
  
-   En Visual Studio 2013, desactive **Habilitar la opción Editar y continuar nativa**.  
  
-   Reinicie ambos equipos.  
  
-   Si la depuración remota requiere proporcionar las credenciales, active la opción para guardar las credenciales.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)