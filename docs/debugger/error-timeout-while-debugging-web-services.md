---
title: 'Error: Tiempo de espera durante la depuración de servicios Web | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f7b97aa665062b0d0388764cb0ab75956087924
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-timeout-while-debugging-web-services"></a>Error: Se excedió el tiempo de espera de depuración de servicios Web
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