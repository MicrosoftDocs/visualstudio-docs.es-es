---
title: 'Error: The web server is not configured correctly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f5df9fb04849fce94d1a82748f2fc88f9577667
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297433"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las causas posibles de este error son:  
  
- Se intentó depurar una aplicación web de .NET que se copió en un equipo diferente, se cambió de nombre manualmente o se movió.  
  
- No hay conexiones IIS suficientes. Para obtener más información sobre cómo implementar un sitio web en IIS, vea [Crear un sitio web](https://docs.microsoft.com/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Si intenta depurar una aplicación ASP.NET, vea [Publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html) para obtener instrucciones sobre la implementación en un equipo remoto que ejecuta IIS 8 o superior, o [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) para obtener instrucciones sobre la implementación en un equipo remoto que ejecuta IIS 7.5.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
