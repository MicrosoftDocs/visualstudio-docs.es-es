---
title: 'Error: Tiempo de espera durante la depuración de servicios Web | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: 98d112528ace581c9173e82af63c502e2124315a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832576"
---
# <a name="error-timeout-while-debugging-web-services"></a>Error: Tiempo de espera de depuración de servicios web agotado
Cuando ejecuta paso a paso un servicio Web XML desde código de llamada, a veces puede excederse el tiempo de espera de la llamada, por lo que no puede continuar la depuración. Puede aparecer un mensaje de error como este:  
  
```cmd
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Soluciones  
 Para evitar este problema, establezca el valor de tiempo de espera de la llamada al servicio Web XML en infinito, como se muestra en este ejemplo:  
  
```csharp
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
