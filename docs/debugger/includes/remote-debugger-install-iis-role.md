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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809463"
---
Estos pasos muestra solo una configuración básica de IIS. Para obtener información más detallada o para instalar en un equipo de escritorio de Windows, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para los sistemas operativos de Windows Server, use el **agregar Roles y características** asistente a través de la **administrar** vínculo o el **panel** vincular en **eladministradordelservidor**. En el paso **Roles de servidor**, active la casilla de **Servidor web (IIS)**.

![El rol Servidor web (IIS) se activa en el paso Seleccionar roles de servidor.](../media/remotedbg-server-roles-ws2012.png)

En el paso **Servicios de rol**, seleccione los servicios de rol IIS que quiera o acepte los servicios de rol predeterminados proporcionados. Si desea habilitar la implementación mediante configuración de publicación y Web Deploy, asegúrese de que **herramientas ni Scripts de administración de IIS** está seleccionada.

Continúe con los pasos de confirmación para instalar el rol de servidor web y servicios. No es necesario reiniciar el servidor ni IIS después de instalar el rol Servidor web (IIS).