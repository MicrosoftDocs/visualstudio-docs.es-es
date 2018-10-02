---
title: 'Error: El servidor web no está configurado correctamente | Microsoft Docs'
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82d827e0f821712306cf1ec6049129fbf4437d67
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581757"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: el servidor web no está configurado correctamente](https://docs.microsoft.com/visualstudio/debugger/error-the-web-server-is-not-configured-correctly).  
  
Las causas posibles de este error son:  
  
-   Se intentó depurar una aplicación web de .NET que se copió en un equipo diferente, se cambió de nombre manualmente o se movió.  
  
-   No hay conexiones IIS suficientes. Para obtener más información sobre cómo implementar un sitio web en IIS, vea [Crear un sitio web](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Si intenta depurar una aplicación ASP.NET, consulte la sección [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html) para obtener instrucciones sobre la implementación en un equipo remoto que ejecuta IIS 8 o posterior, o [Remote Debugging ASP.NET on un Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) para obtener instrucciones sobre la implementación en un equipo remoto que ejecuta IIS 7.5.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



