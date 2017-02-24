---
title: "¿Qué opciones de publicación son las adecuadas para mí? | Microsoft Docs"
ms.custom: 
ms.date: 1/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 85a7f3ef705d3b110ab0dc39d08d0cee235bf307
ms.openlocfilehash: 1ecb87d748a7770101bdf6e0ffe34250a36c97a8

---

# <a name="what-publishing-options-are-right-for-me"></a>¿Qué opciones de publicación son las adecuadas para mí?

Desde Visual Studio, las aplicaciones web pueden publicarse directamente en los destinos siguientes:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Sistema de archivos](#file-system)
- [Destinos personalizados (IIS, FTP, etc.)](#custom-targets), que incluye todos los servidores web arbitrarios.

En la pestaña **Publicar**, puede seleccionar un perfil de publicación existente, importar uno existente o crear uno nuevo con las opciones que se describen aquí. 

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) ayuda a los desarrolladores a crear rápidamente una variedad de aplicaciones y servicios web escalables sin mantener la infraestructura.

Para las aplicaciones web en particular, un App Service es un contenedor para una [*aplicación web*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/), algo que se asemeja mucho a un host web tradicional. Es decir, una aplicación web proporciona los recursos de proceso necesarios que pueden ejecutar su código del lado servidor y hacer que esté disponible en Internet.

Determine la potencia de proceso que tiene una aplicación web eligiendo un [plan de tarifa](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/) para el App Service que la contiene. También tiene varias aplicaciones web (y otros tipos de aplicación) que comparten el mismo App Service sin cambiar el plan de tarifa. Por ejemplo, puede hospedar aplicaciones web de producción, almacenamiento provisional y desarrollo juntas en el mismo App Service. 

Un App Service se ejecuta en máquinas virtuales hospedadas en la nube de Azure, pero es usted quien administra esas máquinas virtuales. A cada aplicación web en un App Service se le asignará una dirección URL única *.azurewebsites.net; todos los planes de tarifa que no sean los gratuitos también permiten personalizar el nombre de dominio del sitio.  

### <a name="when-to-choose-azure-app-service"></a>Cuándo optar por Azure App Service

- Si quiere implementar una aplicación web que sea accesible mediante Internet.
- Si quiere escalar automáticamente la aplicación web en función de la demanda sin necesidad de volver a implementarla.
- Si no quiere mantener una infraestructura de servidor (incluidas las actualizaciones de software).
- Si no necesita ninguna personalización de nivel de máquina en los servidores que hospedan su aplicación web.


> Si quiere usar Azure App Service en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) le permite crear y administrar cualquier cantidad de recursos informáticos en la nube. Al asumir la responsabilidad de todo el software y las actualizaciones de las máquinas virtuales, puede personalizarlas todo lo que quiera según necesite su aplicación web. También puede tener acceso a los servidores directamente mediante Escritorio remoto y cada uno mantendrá su dirección IP asignada durante el tiempo que se quiera.

Escalar una aplicación web que se hospeda en máquinas virtuales implica desarrollar máquinas virtuales adicionales en función de la demanda y, después, implementar el software necesario. Este nivel de control adicional le permite escalar de manera diferente en diferentes regiones del mundo. Por ejemplo, si su aplicación está atendiendo a empleados en una variedad de oficinas regionales, puede escalar sus máquinas virtuales en función del número de empleados de esas regiones, reduciendo potencialmente los costos. 

Para obtener información adicional, vea la [comparación detallada](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) entre Azure App Service, Azure Virtual Machines y otros servicios de Azure que puede usar como un destino de implementación mediante la opción Personalizar de Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Cuándo optar por Azure App Virtual Machines

- Si quiere implementar una aplicación web que sea accesible desde Internet, con un control completo sobre la duración de las direcciones IP asignadas.
- Si necesita personalizaciones de nivel de máquina en sus servidores, que incluyen software adicional como un sistema de base de datos especializado, configuraciones de red específicas, particiones de disco, etc.
- Si quiere tener un control exhaustivo sobre la escalación de su aplicación web.
- Si necesita acceso directo a los servidores que hospedan su aplicación por cualquier otro motivo.

> Si quiere usar Azure Virtual Machines en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## <a name="file-system"></a>Sistema de archivos

Implementar en el sistema de archivos significa simplemente copiar los archivos de su aplicación web en una carpeta específica de su propio equipo. A menudo se usa con fines de prueba, o para implementar la aplicación y que la usen un número limitado de usuarios si el equipo también está ejecutando un servidor web. Si la carpeta de destino se comparte en una red, entonces la implementación en el sistema de archivos también puede hacer que los archivos de la aplicación web estén disponibles para otros usuarios que puedan implementarla después en servidores específicos.  

Cualquier máquina local que esté ejecutando un servidor web puede hacer que su aplicación esté disponible en Internet o en una intranet, dependiendo de cómo esté configurada y de las redes a las que esté conectada. (Si conecta un equipo directamente en Internet, preste especial atención a protegerlo de amenazas de seguridad externas). Como administra estas máquinas, tiene el control completo de las configuraciones de software y hardware. 

Tenga en cuenta que si por cualquier razón (como el acceso a la máquina) no puede usar servicios en la nube como Azure App Service o Azure Virtual Machines, puede usar [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) en su propio centro de datos. Azure Stack le permite administrar y usar los recursos informáticos mediante Azure App Service y Azure Virtual Machines mientras se sigue conservando todo en el entorno local.  

### <a name="when-to-choose-file-system-deployment"></a>Cuándo optar por la implementación del sistema de archivos

- Si solo necesita implementar la aplicación en un recurso compartido de archivos desde el que otros usuarios la implementarán en diferentes servidores.
- Si solo necesita una implementación de pruebas locales.
- Si quiere examinar y modificar potencialmente los archivos de aplicación independientemente antes de enviarlos a otro destino de implementación.



## <a name="custom-targets"></a>Destinos personalizados

Un destino personalizado le permite implementar su aplicación web en un destino que no sea Azure App Service, Azure Virtual Machines o el sistema de archivos local. Puede implementar en un sistema de archivos o en cualquier otro servidor (Internet o intranet) al que tenga acceso, incluidos los que se encuentran en otros servicios en la nube. Puede funcionar con implementación web (archivos o .ZIP) y FTP. 

Cuando elige un destino personalizado, Visual Studio le pide un nombre de perfil y, después, recopila información de **conexión** adicional, incluido el servidor de destino o la ubicación, un nombre de sitio y las credenciales. También puede controlar determinados comportamientos en la pestaña **Configuración**, como la configuración que quiere implementar, si quiere quitar archivos existentes del destino, si quiere precompilar durante la publicación y si quiere excluir archivos en la carpeta App_Data de la implementación. 

Puede crear cualquier número de perfiles de implementación personalizados en Visual Studio, lo que hace que sea posible administrar perfiles con una configuración ligeramente diferente si es necesario.

### <a name="when-to-choose-custom-deployment"></a>Cuándo optar por la implementación personalizada

- Si está usando servicios en la nube en un proveedor que no sea Azure a los que se puede acceder mediante direcciones URL.
- Si quiere implementar con credenciales que no sean las que usa con Visual Studio ni las que están asociadas directamente a las cuentas de Azure.
- Si quiere eliminar archivos del destino cada vez que implementa. 




<!--HONumber=Feb17_HO4-->


