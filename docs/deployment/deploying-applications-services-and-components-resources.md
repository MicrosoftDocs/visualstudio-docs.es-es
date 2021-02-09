---
title: Implementación de una aplicación de Visual Studio en una carpeta, IIS, Azure u otro destino
titleSuffix: ''
description: Obtenga más información sobre las opciones de publicación de la aplicación con la herramienta de publicación.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7e0a8e8a313e351d175822e2427378fb89703444
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879233"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Implementación de la aplicación en una carpeta, IIS, Azure u otro destino

Al implementar una aplicación, servicio o componente, se distribuye para su instalación en otros equipos, dispositivos, servidores o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita.

Obtenga ayuda para la tarea de implementación:

- ¿No está seguro de qué opción de implementación elegir? Consulte [¿Qué opciones de publicación son las adecuadas para mí?](#what-publishing-options-are-right-for-me)
- Para ayuda con los problemas de implementación de Azure App Service o IIS, consulte [Solución de problemas de ASP.NET Core en Azure App Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).
- Para obtener ayuda con la configuración de la implementación de .NET, vea [Configuración de la implementación de .NET](#configure-net-deployment-settings).
- Para implementar un destino nuevo, si creó previamente un perfil de publicación, seleccione **Nuevo** en la ventana **Publicar** de un perfil configurado.

   ![Creación de un perfil de publicación nuevo](../deployment/media/create-a-new-publish-profile.png)

   Luego, elija una opción de implementación en la ventana Publicar. Para información sobre las opciones de publicación, consulte las secciones siguientes.

## <a name="what-publishing-options-are-right-for-me"></a>¿Qué opciones de publicación son las adecuadas para mí?

Desde Visual Studio, las aplicaciones pueden publicarse directamente en los destinos siguientes:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Container Registry para Docker](#docker-container-registry)
- [Carpeta](#folder)
- [Servidor FTP/FTPS](#ftpftps-server)
- [Servidor web (IIS)](#web-server-iis)
- [Perfil de importación](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service en Linux](#azure-app-service)
- [IIS (elección de IIS, FTP, etc.)](#web-server-iis)
- [FTP/FTPS (elección de IIS, FTP, etc.)](#ftpftps-server)
- [Carpeta](#folder)
- [Perfil de importación](#import-profile)
::: moniker-end

Las opciones anteriores aparecen tal como se muestra en la ilustración siguiente cuando se crea un perfil de publicación nuevo.

::: moniker range=">=vs-2019"
![Elección de una opción de publicación](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Elección de una opción de publicación](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Para un paseo rápido por más opciones generales de implementación de aplicaciones, consulte [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Cuando elige Azure, puede elegir entre:

- [Azure App Service](#azure-app-service) que se ejecuta en Windows, Linux o como una imagen de Docker
- Una imagen de Docker implementada en [Azure Container Registry](#azure-container-registry)
- Una [máquina virtual de Azure](#azure-virtual-machine)

![Elección de un servicio de Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) ayuda a los desarrolladores a crear rápidamente una variedad de aplicaciones y servicios web escalables sin mantener la infraestructura. Un App Service se ejecuta en máquinas virtuales hospedadas en la nube de Azure, pero es usted quien administra esas máquinas virtuales. A cada aplicación web de una instancia de App Service se le asigna una dirección URL única \*.azurewebsites.net; todos los planes de tarifa menos el gratuito permiten asignar nombres de dominio personalizados al sitio.

El usuario determina la potencia de computación de una instancia de App Service al elegir un [plan de tarifa](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) para la instancia de App Service que la contiene. Puede hacer que varias aplicaciones web (y otros tipos de aplicaciones) compartan la misma instancia de App Service sin cambiar el plan de tarifa. Por ejemplo, puede hospedar aplicaciones web de desarrollo, almacenamiento provisional y producción en la misma instancia de App Service.

#### <a name="when-to-choose-azure-app-service"></a>Cuándo optar por Azure App Service

- Si quiere implementar una aplicación web que sea accesible mediante Internet.
- Si quiere escalar automáticamente la aplicación web en función de la demanda sin necesidad de volver a implementarla.
- Si no quiere mantener una infraestructura de servidor (incluidas las actualizaciones de software).
- Si no necesita ninguna personalización de nivel de máquina en los servidores que hospedan su aplicación web.

> Si quiere usar Azure App Service en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Para más información sobre cómo publicar en App Service, consulte:
- [Inicio rápido: Publicar una aplicación web en Azure App Service mediante Visual Studio](quickstart-deploy-to-azure.md)
- [Inicio rápido: Publicar una aplicación de ASP.NET Core en App Service en Linux con Visual Studio](quickstart-deploy-to-linux.md)
- [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Solución de problemas de ASP.NET Core en Azure App Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) permite compilar, almacenar y administrar imágenes y artefactos de contenedor de Docker en un registro privado para todo tipo de implementaciones de contenedor.

#### <a name="when-to-choose-azure-container-registry"></a>Cuándo elegir Azure Container Registry

- Cuando tenga una canalización de implementación y desarrollo de contenedores de Docker existente.
- Cuando quiera compilar imágenes de contenedor de Docker en Azure.

Para obtener más información:

- [Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Máquina virtual de Azure

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) permite crear y administrar cualquier cantidad de recursos informáticos en la nube. Al asumir la responsabilidad de todo el software y las actualizaciones de las máquinas virtuales, puede personalizarlas todo lo que quiera según necesite la aplicación. Puede tener acceso a las máquinas virtuales directamente mediante Escritorio remoto, y cada una mantendrá su dirección IP asignada durante el tiempo que se quiera.

El escalado de una aplicación hospedada en máquinas virtuales implica activar otras máquinas virtuales en función de la demanda y luego implementar el software necesario. Este nivel de control adicional le permite escalar de manera diferente en diferentes regiones del mundo. Por ejemplo, si su aplicación está atendiendo a empleados en una variedad de oficinas regionales, puede escalar sus máquinas virtuales en función del número de empleados de esas regiones, reduciendo potencialmente los costos.

Para obtener información adicional, vea la [comparación detallada](/azure/architecture/guide/technology-choices/compute-decision-tree) entre Azure App Service, Azure Virtual Machines y otros servicios de Azure que puede usar como destino de implementación mediante la opción Personalizar de Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Cuándo elegir Azure Virtual Machines

- Si quiere implementar una aplicación web que sea accesible desde Internet, con un control completo sobre la duración de las direcciones IP asignadas.
- Se necesitan personalizaciones de nivel de máquina en los servidores, lo que incluye software adicional como un sistema de base de datos especializado, configuraciones de red específicas, particiones de disco, etc.
- Si quiere tener un control exhaustivo sobre la escalación de su aplicación web.
- Si necesita acceso directo a los servidores que hospedan su aplicación por cualquier otro motivo.

> Si quiere usar Azure Virtual Machines en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Registro de contenedor de Docker

Si la aplicación usa Docker, puede publicar la aplicación en contenedores en un registro de contenedor de Docker.

### <a name="when-to-choose-docker-container-registry"></a>Cuándo elegir Container Registry para Docker

- Quiere implementar una aplicación en contenedores.

Para obtener más información, vea lo siguiente:

- [Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](../containers/hosting-web-apps-in-docker.md)
- [Implementación en Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Carpeta

Una implementación en el sistema de archivos conlleva copiar los archivos de la aplicación en una carpeta determinada del equipo propio. A menudo, la implementación en una carpeta se usa con fines de prueba o para implementar la aplicación para que la use un número limitado de usuarios si el equipo también ejecuta un servidor. Si la carpeta de destino se comparte en una red, la implementación en el sistema de archivos puede hacer que los archivos de la aplicación web estén disponibles para otros usuarios que, a su vez, podrán implementarla después en servidores específicos.
::: moniker range=">=vs-2019"
A partir de Visual Studio 2019 16.8, el destino de carpeta ofrece la posibilidad de publicar una aplicación Windows de .NET mediante ClickOnce.

Si quiere publicar una aplicación Windows de .NET Core 3.1 o más reciente con ClickOnce, vea [Implementación de una aplicación Windows de .NET con ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Cualquier máquina local que esté ejecutando un servidor puede hacer que la aplicación esté disponible en Internet o en una intranet, según cómo esté configurada y de las redes a las que esté conectada. (Si conecta un equipo directamente en Internet, preste especial atención a protegerlo de amenazas de seguridad externas). Como administra estas máquinas, tiene el control completo de las configuraciones de software y hardware.

Si por alguna razón (como el acceso a la máquina) no puede usar servicios en la nube como Azure App Service o Azure Virtual Machines, puede emplear [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) en el centro de datos propio. Azure Stack le permite administrar y usar los recursos informáticos mediante Azure App Service y Azure Virtual Machines mientras se sigue conservando todo en el entorno local.

### <a name="when-to-choose-file-system-deployment"></a>Cuándo optar por la implementación del sistema de archivos

- Si solo necesita implementar la aplicación en un recurso compartido de archivos desde el que otros usuarios la implementarán en diferentes servidores.
::: moniker range=">=vs-2019"
- Si quiere implementar una aplicación Windows de .NET con ClickOnce.
::: moniker-end
- Si solo necesita una implementación de pruebas locales.
- Si quiere examinar y modificar potencialmente los archivos de aplicación independientemente antes de enviarlos a otro destino de implementación.

Para más información, consulte [Inicio rápido: Implementar una aplicación en una carpeta local con Visual Studio](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
Para obtener más información sobre la implementación de una aplicación Windows de .NET mediante ClickOnce, vea [Implementación de una aplicación Windows de .NET con ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Para más ayuda sobre cómo elegir la configuración, consulte los recursos siguientes:

- [Implementación dependiente del marco frente a la implementación independiente](/dotnet/core/deploying/)
- [Identificadores de entorno de ejecución de destino (RID portátil, etc.)](/dotnet/core/rid-catalog)
- [Configuraciones Debug y Release](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Servidor FTP/FTPS

Un servidor FTP/FTPS permite implementar la aplicación en un servidor que no sea Azure. Puede implementar en un sistema de archivos o en cualquier otro servidor (Internet o intranet) al que tenga acceso, incluidos los que se encuentran en otros servicios en la nube. Puede funcionar con implementación web (archivos o .ZIP) y FTP.

Al elegir un servidor FTP/FTPS, Visual Studio le pide un nombre de perfil y luego recopila información de **Conexión** adicional, incluido el servidor de destino o la ubicación, un nombre de sitio y las credenciales. Puede controlar los siguientes comportamientos en pestaña **Configuración**:

- La configuración que desea implementar.
- Si desea quitar los archivos existentes del destino.
- Si desea precompilar durante la publicación.
- Si desea excluir archivos en la carpeta App_Data de la implementación.

Puede crear cualquier número de perfiles de implementación de FTP/FTPS en Visual Studio, lo que hace que sea posible administrar perfiles con diferentes configuraciones.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Cuándo elegir la implementación de servidor FTP/FTPS

- Usa servicios en la nube en un proveedor que no es Azure a los que se puede acceder mediante direcciones URL.
- Si quiere implementar con credenciales que no sean las que usa con Visual Studio ni las que están asociadas directamente a las cuentas de Azure.
- Si quiere eliminar archivos del destino cada vez que implementa.

## <a name="web-server-iis"></a>Servidor web (IIS)

Un servidor web IIS permite implementar la aplicación en un servidor que no sea Azure. Puede implementar en un servidor IIS (Internet o intranet) al que tenga acceso, incluidos los que se encuentran en otros servicios en la nube. Puede funcionar con Web Deploy o con un paquete de Web Deploy.

Al elegir un servidor web IIS, Visual Studio le pide un nombre de perfil y luego recopila información de **Conexión** adicional, incluido el servidor de destino o la ubicación, un nombre de sitio y las credenciales. Puede controlar los siguientes comportamientos en pestaña **Configuración**:

- La configuración que desea implementar.
- Si desea quitar los archivos existentes del destino.
- Si desea precompilar durante la publicación.
- Si desea excluir archivos en la carpeta App_Data de la implementación.

Puede crear cualquier número de perfiles de implementación de servidor web IIS en Visual Studio, lo que hace que sea posible administrar perfiles con diferentes configuraciones.

### <a name="when-to-choose-web-server-iis-deployment"></a>Cuándo elegir la implementación de servidor web (IIS)

- Si usa IIS para publicar un sitio o servicio al que se puede acceder a través de direcciones URL.
- Si quiere implementar con credenciales que no sean las que usa con Visual Studio ni las que están asociadas directamente a las cuentas de Azure.
- Si quiere eliminar archivos del destino cada vez que implementa.

Para más información, consulte [Inicio rápido: Publicar una aplicación web en un sitio web mediante Visual Studio](quickstart-deploy-to-a-web-site.md).

Para obtener ayuda con la solución de problemas de ASP.NET Core en IIS, vea [Solución de problemas de ASP.NET Core en Azure App Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Perfil de importación

Puede importar un perfil cuando realice la implementación en IIS o Azure App Service. Puede configurar la implementación con un *archivo de configuración de publicación* ( *\*.publishsettings*). Un archivo de configuración de publicación se crea mediante IIS o Azure App Service, o puede crearse manualmente y después importarse en Visual Studio.

El uso de un archivo de configuración de publicación puede simplificar la configuración de la implementación y funciona mejor en un entorno de equipo en comparación con la configuración manual de cada perfil de implementación.

### <a name="when-to-choose-import-profile"></a>Cuándo elegir el perfil de importación

- Si publica en IIS y quiere simplificar la configuración de la implementación.
- Si publica en IIS o Azure App Service y quiere acelerar la configuración de la implementación para volver a usarla o para los miembros del equipo que publican en el mismo servicio.

Para obtener más información, vea lo siguiente:

- [Importar una configuración de publicación e implementar en IIS](tutorial-import-publish-settings-iis.md)
- [Importar una configuración de publicación e implementar en Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Configuración de la implementación de .NET

Para más ayuda sobre cómo elegir la configuración, consulte los recursos siguientes:

- [Implementación dependiente del marco frente a la implementación independiente](/dotnet/core/deploying/)
- [Identificadores de entorno de ejecución de destino (RID portátil, etc.)](/dotnet/core/rid-catalog)
- [Configuraciones Debug y Release](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Pasos siguientes

Tutoriales:

- [Implementar una aplicación .NET Core con la herramienta de publicación](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Implementación en Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Empaquetar una aplicación para UWP con Visual Studio](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publish a Node.js app to Azure using Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json) (Publicar una aplicación Node.js en Azure mediante Web Deploy)
- [Publicación en Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
