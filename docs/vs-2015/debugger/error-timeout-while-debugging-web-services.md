---
title: 'Error: Tiempo de espera durante la depuración de servicios Web | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578318"
---
# <a name="error-timeout-while-debugging-web-services"></a>Error: Se excedió el tiempo de espera de depuración de servicios Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: Timeout While Debugging Web Services](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
Cuando ejecuta paso a paso un servicio Web XML desde código de llamada, a veces puede excederse el tiempo de espera de la llamada, por lo que no puede continuar la depuración. Puede aparecer un mensaje de error como este:  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Soluciones  
 Para evitar este problema, establezca el valor de tiempo de espera de la llamada al servicio Web XML en infinito, como se muestra en este ejemplo:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



