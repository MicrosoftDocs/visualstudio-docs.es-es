---
title: 'Error: Tiempo de espera de depuración de servicios web agotado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efb77689c33d263723f146f9b2484748505406b6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460278"
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
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
