---
title: 'Información general de implementación: Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7346de998052ba68dfadf74a09fe0d4339be1614
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757167"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Información general de implementación en Visual Studio

Al implementar una aplicación, servicio o componente, se distribuye para su instalación en otros equipos, dispositivos, servidores o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita.

Para muchos tipos comunes de aplicación, puede implementar su aplicación directamente desde el Explorador de soluciones en Visual Studio. Para una visita rápida por esta funcionalidad, consulte [primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md).

![Elija una opción de publicación](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>¿Qué opciones de publicación son las adecuadas para mí?

Desde dentro de Visual Studio, las aplicaciones pueden publicarse directamente en los destinos siguientes:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Sistema de archivos](#file-system)
- [Destinos personalizados (IIS, FTP, etc.)](#custom-targets), que incluye todos los servidores web arbitrarios.

En la pestaña **Publicar**, puede seleccionar un perfil de publicación existente, importar uno existente o crear uno nuevo con las opciones que se describen aquí. Para ver las opciones de publicación en el IDE para tipos diferentes de aplicaciones, consulte [Inicio rápido: Busque primero en la implementación en Visual Studio](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) ayuda a los desarrolladores a crear rápidamente una variedad de aplicaciones y servicios web escalables sin mantener la infraestructura.

Determinar la potencia de un servicio de aplicaciones de proceso tiene eligiendo un [plan de tarifa](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) para el servicio de aplicación que lo contiene. Puede tener varias Web apps (y otros tipos de aplicaciones) que comparten el mismo App Service sin cambiar el plan de tarifa. Por ejemplo, puede hospedar aplicaciones Web de desarrollo, ensayo y producción juntos en el mismo App Service.

Un App Service se ejecuta en máquinas virtuales hospedadas en la nube de Azure, pero es usted quien administra esas máquinas virtuales. Cada aplicación en un App Service se le asignará un único \*. dirección URL de azurewebsites.net; todos los planes precios que no sea gratis permiten asignar nombres de dominio personalizados al sitio.

### <a name="when-to-choose-azure-app-service"></a>Cuándo optar por Azure App Service

- Si quiere implementar una aplicación web que sea accesible mediante Internet.
- Si quiere escalar automáticamente la aplicación web en función de la demanda sin necesidad de volver a implementarla.
- Si no quiere mantener una infraestructura de servidor (incluidas las actualizaciones de software).
- Si no necesita ninguna personalización de nivel de máquina en los servidores que hospedan su aplicación web.

> Si quiere usar Azure App Service en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Para obtener más información sobre la publicación en App Service, consulte [inicio rápido: publicar en Azure App Service](quickstart-deploy-to-azure.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) le permite crear y administrar cualquier cantidad de recursos informáticos en la nube. Al asumir la responsabilidad para todo el software y actualizaciones en las máquinas virtuales, puede personalizarlas tanto como quiera según necesite su aplicación. Puede tener acceso a las máquinas virtuales directamente mediante Escritorio remoto, y cada una mantendrá su dirección IP asignada durante el tiempo que se quiera.

Escalar una aplicación que se hospeda en máquinas virtuales implica desarrollar máquinas virtuales adicionales según la demanda y, a continuación, implementar el software necesario. Este nivel de control adicional le permite escalar de manera diferente en diferentes regiones del mundo. Por ejemplo, si su aplicación está atendiendo a empleados en una variedad de oficinas regionales, puede escalar sus máquinas virtuales en función del número de empleados de esas regiones, reduciendo potencialmente los costos.

Para obtener información adicional, vea la [comparación detallada](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) entre Azure App Service, Azure Virtual Machines y otros servicios de Azure que puede usar como un destino de implementación mediante la opción Personalizar de Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Cuándo optar por Azure App Virtual Machines

- Si quiere implementar una aplicación web que sea accesible desde Internet, con un control completo sobre la duración de las direcciones IP asignadas.
- Si necesita personalizaciones de nivel de máquina en sus servidores, que incluyen software adicional como un sistema de base de datos especializado, configuraciones de red específicas, particiones de disco, etc.
- Si quiere tener un control exhaustivo sobre la escalación de su aplicación web.
- Si necesita acceso directo a los servidores que hospedan su aplicación por cualquier otro motivo.

> Si quiere usar Azure Virtual Machines en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Sistema de archivos

Implementación en el sistema de archivos significa simplemente copiar los archivos de la aplicación en una carpeta específica en su propio equipo. Esto se suele utilizar con fines de prueba, o para implementar la aplicación para su uso por un número limitado de usuarios si el equipo también se está ejecutando un servidor. Si la carpeta de destino se comparte en una red, la implementación en el sistema de archivos puede hacer que los archivos de la aplicación web estén disponibles para otros usuarios que, a su vez, podrán implementarla después en servidores específicos.

Cualquier máquina local que está ejecutando un servidor, la aplicación puede quedar disponibles a través de Internet o una Intranet según cómo esté configurada y las redes a la que está conectado. (Si conecta un equipo directamente en Internet, preste especial atención a protegerlo de amenazas de seguridad externas). Como administra estas máquinas, tiene el control completo de las configuraciones de software y hardware.

Tenga en cuenta que si por cualquier razón (como el acceso a la máquina) no puede usar servicios en la nube como Azure App Service o Azure Virtual Machines, puede usar [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) en su propio centro de datos. Azure Stack le permite administrar y usar los recursos informáticos mediante Azure App Service y Azure Virtual Machines mientras se sigue conservando todo en el entorno local.

### <a name="when-to-choose-file-system-deployment"></a>Cuándo optar por la implementación del sistema de archivos

- Si solo necesita implementar la aplicación en un recurso compartido de archivos desde el que otros usuarios la implementarán en diferentes servidores.
- Si solo necesita una implementación de pruebas locales.
- Si quiere examinar y modificar potencialmente los archivos de aplicación independientemente antes de enviarlos a otro destino de implementación.

Para obtener más información, consulte [inicio rápido: implementación en una carpeta local](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Destinos personalizados (IIS, FTP)

Un destino personalizado le permite implementar la aplicación en un destino distinto de Azure App Service, Azure Virtual Machines o el sistema de archivos local. Puede implementar en un sistema de archivos o en cualquier otro servidor (Internet o intranet) al que tenga acceso, incluidos los que se encuentran en otros servicios en la nube. Puede funcionar con implementación web (archivos o .ZIP) y FTP.

Cuando elige un destino personalizado, Visual Studio le pide un nombre de perfil y, después, recopila información de **conexión** adicional, incluido el servidor de destino o la ubicación, un nombre de sitio y las credenciales. Puede controlar los siguientes comportamientos en pestaña **Configuración**:

- La configuración que desea implementar.
- Si desea quitar los archivos existentes del destino.
- Si desea precompilar durante la publicación.
- Si desea excluir archivos en la carpeta App_Data de la implementación.

Puede crear cualquier número de perfiles de implementación personalizados en Visual Studio, lo que hace que sea posible administrar perfiles con diferentes configuraciones.

### <a name="when-to-choose-custom-deployment"></a>Cuándo optar por la implementación personalizada

- Usa servicios en la nube en un proveedor que no es Azure a los que se puede acceder mediante direcciones URL.
- Si quiere implementar con credenciales que no sean las que usa con Visual Studio ni las que están asociadas directamente a las cuentas de Azure.
- Si quiere eliminar archivos del destino cada vez que implementa.

Para obtener más información, consulte [inicio rápido: implementación en un sitio web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Pasos siguientes

Tutoriales:

- [Implementar una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publicar una aplicación ASP.NET core en Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Implementación en Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Implementar aplicaciones de UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publicar una aplicación Node.js en Azure con Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publicar una aplicación de Python en Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
