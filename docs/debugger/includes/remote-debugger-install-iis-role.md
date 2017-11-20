---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
Estos pasos muestran solo una configuración básica de IIS. Para obtener información más detallada o para instalar en un equipo de escritorio de Windows, vea [publicar en IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para sistemas operativos de Windows Server, use la **agregar Roles y características** asistente a través de la **administrar** vínculo o **panel** vincular en **eladministradordelservidor**. En el paso **Roles de servidor**, active la casilla de **Servidor web (IIS)**.

![El rol Servidor web (IIS) se activa en el paso Seleccionar roles de servidor.](../media/remotedbg-server-roles-ws2012.png)

En el paso **Servicios de rol**, seleccione los servicios de rol IIS que quiera o acepte los servicios de rol predeterminados proporcionados.

Continúe con los pasos de confirmación para instalar el rol de servidor web y servicios. No es necesario reiniciar el servidor ni IIS después de instalar el rol Servidor web (IIS).