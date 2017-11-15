---
title: "¿Qué opciones de publicación son las adecuadas para mí? | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.reviewer: riande
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: "1"
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16bc087e6c4a12d3f70e2e71ba644faab9567fee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# ¿Qué opciones de publicación son las adecuadas para mí?

Desde Visual Studio, las aplicaciones web pueden publicarse directamente en los destinos siguientes:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Sistema de archivos](#file-system)
- [Destinos personalizados (IIS, FTP, etc.)](#custom-targets), que incluye todos los servidores web arbitrarios.

En la pestaña **Publicar**, puede seleccionar un perfil de publicación existente, importar uno existente o crear uno nuevo con las opciones que se describen aquí.

## Azure App Service

[Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) ayuda a los desarrolladores a crear rápidamente una variedad de aplicaciones y servicios web escalables sin mantener la infraestructura.

Para las aplicaciones web en particular, un App Service es un contenedor para una [*aplicación web*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/), algo que se asemeja mucho a un host web tradicional. Es decir, una aplicación web proporciona los recursos de proceso necesarios que pueden ejecutar su código del lado servidor y hacer que esté disponible en Internet.

Determine la potencia de proceso que tiene una aplicación web eligiendo un [plan de tarifa](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/) para el App Service que la contiene. Puede tener varias aplicaciones web (y otros tipos de aplicación) que comparten el mismo App Service sin cambiar el plan de tarifa. Por ejemplo, puede hospedar aplicaciones web de producción, almacenamiento provisional y desarrollo juntas en el mismo App Service.

Un App Service se ejecuta en máquinas virtuales hospedadas en la nube de Azure, pero es usted quien administra esas máquinas virtuales. A cada aplicación web en un App Service se le asignará una dirección URL única \*.azurewebsites.net; todos los planes de tarifa que no sean los gratuitos también permiten asignar nombres de dominio personalizados al sitio.

### Cuándo optar por Azure App Service

- Si quiere implementar una aplicación web que sea accesible mediante Internet.
- Si quiere escalar automáticamente la aplicación web en función de la demanda sin necesidad de volver a implementarla.
- Si no quiere mantener una infraestructura de servidor (incluidas las actualizaciones de software).
- Si no necesita ninguna personalización de nivel de máquina en los servidores que hospedan su aplicación web.


> Si quiere usar Azure App Service en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) le permite crear y administrar cualquier cantidad de recursos informáticos en la nube. Al asumir la responsabilidad de todo el software y las actualizaciones de las máquinas virtuales, puede personalizarlas todo lo que quiera según necesite su aplicación web. Puede tener acceso a las máquinas virtuales directamente mediante Escritorio remoto, y cada una mantendrá su dirección IP asignada durante el tiempo que se quiera.

Escalar una aplicación web que se hospeda en máquinas virtuales implica desarrollar máquinas virtuales adicionales en función de la demanda y, después, implementar el software necesario. Este nivel de control adicional le permite escalar de manera diferente en diferentes regiones del mundo. Por ejemplo, si su aplicación está atendiendo a empleados en una variedad de oficinas regionales, puede escalar sus máquinas virtuales en función del número de empleados de esas regiones, reduciendo potencialmente los costos.

Para obtener información adicional, vea la [comparación detallada](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) entre Azure App Service, Azure Virtual Machines y otros servicios de Azure que puede usar como un destino de implementación mediante la opción Personalizar de Visual Studio.

### Cuándo optar por Azure App Virtual Machines

- Si quiere implementar una aplicación web que sea accesible desde Internet, con un control completo sobre la duración de las direcciones IP asignadas.
- Si necesita personalizaciones de nivel de máquina en sus servidores, que incluyen software adicional como un sistema de base de datos especializado, configuraciones de red específicas, particiones de disco, etc.
- Si quiere tener un control exhaustivo sobre la escalación de su aplicación web.
- Si necesita acceso directo a los servidores que hospedan su aplicación por cualquier otro motivo.

> Si quiere usar Azure Virtual Machines en su propio centro de datos o en otros equipos locales, puede hacerlo con [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## Sistema de archivos

Implementar en el sistema de archivos significa simplemente copiar los archivos de su aplicación web en una carpeta específica de su propio equipo. A menudo se usa con fines de prueba, o para implementar la aplicación y que la usen un número limitado de usuarios si el equipo también está ejecutando un servidor web. Si la carpeta de destino se comparte en una red, la implementación en el sistema de archivos puede hacer que los archivos de la aplicación web estén disponibles para otros usuarios que, a su vez, podrán implementarla después en servidores específicos.

Cualquier máquina local que esté ejecutando un servidor web puede hacer que su aplicación esté disponible en Internet o en una intranet, dependiendo de cómo esté configurada y de las redes a las que esté conectada. (Si conecta un equipo directamente en Internet, preste especial atención a protegerlo de amenazas de seguridad externas). Como administra estas máquinas, tiene el control completo de las configuraciones de software y hardware.

Tenga en cuenta que si por cualquier razón (como el acceso a la máquina) no puede usar servicios en la nube como Azure App Service o Azure Virtual Machines, puede usar [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) en su propio centro de datos. Azure Stack le permite administrar y usar los recursos informáticos mediante Azure App Service y Azure Virtual Machines mientras se sigue conservando todo en el entorno local.

### Cuándo optar por la implementación del sistema de archivos

- Si solo necesita implementar la aplicación en un recurso compartido de archivos desde el que otros usuarios la implementarán en diferentes servidores.
- Si solo necesita una implementación de pruebas locales.
- Si quiere examinar y modificar potencialmente los archivos de aplicación independientemente antes de enviarlos a otro destino de implementación.



## Destinos personalizados

Un destino personalizado le permite implementar su aplicación web en un destino que no sea Azure App Service, Azure Virtual Machines o el sistema de archivos local. Puede implementar en un sistema de archivos o en cualquier otro servidor (Internet o intranet) al que tenga acceso, incluidos los que se encuentran en otros servicios en la nube. Puede funcionar con implementación web (archivos o .ZIP) y FTP.

Cuando elige un destino personalizado, Visual Studio le pide un nombre de perfil y, después, recopila información de **conexión** adicional, incluido el servidor de destino o la ubicación, un nombre de sitio y las credenciales. Puede controlar los siguientes comportamientos en pestaña **Configuración**:

- La configuración que desea implementar.
- Si desea quitar los archivos existentes del destino.
- Si desea precompilar durante la publicación.
- Si desea excluir archivos en la carpeta App_Data de la implementación.

Puede crear cualquier número de perfiles de implementación personalizados en Visual Studio, lo que hace que sea posible administrar perfiles con diferentes configuraciones.

### Cuándo optar por la implementación personalizada

- Si está usando servicios en la nube en un proveedor que no sea Azure a los que se puede acceder mediante direcciones URL.
- Si quiere implementar con credenciales que no sean las que usa con Visual Studio ni las que están asociadas directamente a las cuentas de Azure.
- Si quiere eliminar archivos del destino cada vez que implementa.
