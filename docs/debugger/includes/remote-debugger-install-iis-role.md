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
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149224"
---
En estos pasos solo muestran una configuración básica de IIS. Para obtener información más detallada o para instalar en un equipo de escritorio de Windows, vea [Publicación en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 Uso de ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

En los sistemas operativos Windows Server, use el asistente **Agregar roles y características** a través del vínculo **Administrar** o el vínculo **Panel** en el **Administrador del servidor**. En el paso **Roles de servidor**, active la casilla de **Servidor web (IIS)** .

![El rol Servidor web (IIS) se activa en el paso Seleccionar roles de servidor.](../media/remotedbg-server-roles-ws2012.png)

En el paso **Servicios de rol**, seleccione los servicios de rol IIS que quiera o acepte los servicios de rol predeterminados proporcionados. Si desea habilitar la implementación con la configuración de publicación y Web Deploy, asegúrese de que la opción **Scripts y herramientas de administración de IIS** esté seleccionada.

Continúe con los pasos de confirmación para instalar el rol y los servicios de servidor web. No es necesario reiniciar el servidor ni IIS después de instalar el rol Servidor web (IIS).