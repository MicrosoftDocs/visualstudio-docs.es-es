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
ms.openlocfilehash: 62bdcd8109263cc86e13484d146e46f8e95c7198
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
Estos pasos muestran solo una configuración básica de IIS. Para obtener información más detallada o para instalar en un equipo de escritorio de Windows, vea [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para sistemas operativos de Windows Server, use la **agregar Roles y características** asistente a través de la **administrar** vínculo o **panel** vincular en **eladministradordelservidor**. En el paso **Roles de servidor**, active la casilla de **Servidor web (IIS)**.

![El rol Servidor web (IIS) se activa en el paso Seleccionar roles de servidor.](../media/remotedbg-server-roles-ws2012.png)

En el paso **Servicios de rol**, seleccione los servicios de rol IIS que quiera o acepte los servicios de rol predeterminados proporcionados. Si planea implementar con Web Deploy, asegúrese de que **herramientas ni Scripts de administración de IIS** está seleccionada.

Continúe con los pasos de confirmación para instalar el rol de servidor web y servicios. No es necesario reiniciar el servidor ni IIS después de instalar el rol Servidor web (IIS).