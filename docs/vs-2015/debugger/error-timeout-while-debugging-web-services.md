---
title: 'Error: Tiempo de espera durante la depuración de servicios Web | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 985082d675da2a56d9880414809d91e92cb1fe0d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736343"
---
# <a name="error-timeout-while-debugging-web-services"></a>Error: Se excedió el tiempo de espera de depuración de servicios Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



