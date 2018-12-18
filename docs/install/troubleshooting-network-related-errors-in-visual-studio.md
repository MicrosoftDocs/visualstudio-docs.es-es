---
title: Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio
description: Busque soluciones para los errores relacionados con la red o con el proxy que puede experimentar al instalar o usar Visual Studio detrás de un firewall o un servidor proxy.
ms.custom: ''
ms.date: 02/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28c92fdc09320effcb8603c42edcfca152f71248
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672319"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio

Tenemos soluciones para la mayoría de los errores típicos relacionados con la red o con el proxy que puede encontrar cuando instala o usa Visual Studio detrás de un firewall o un servidor proxy.

## <a name="error-proxy-authorization-required"></a>Error: Se necesita autorización de proxy

Por lo general, este error se produce cuando los usuarios están conectados a Internet a través de un servidor proxy y este bloquea las llamadas que hace Visual Studio a algunos recursos de red.

### <a name="to-fix-this-proxy-error"></a>Para corregir este error de proxy

- Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales cuando se le solicite en el cuadro de diálogo.

- Si el reinicio de Visual Studio no soluciona el problema, es posible que el servidor proxy no pida credenciales para direcciones http:&#47;&#47;go.microsoft.com pero sí lo hace para direcciones &#42;.direcciones visualStudio.com. Para estos servidores, considere incluir en una lista blanca las siguientes direcciones URL para desbloquear todos los escenarios de inicio de sesión en Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- En caso contrario puede quitar la dirección http:&#47;&#47;go.microsoft.com  de la lista de permitidos para que el cuadro de diálogo de autenticación de proxy aparezca para la direcciónhttp:&#47;&#47;go.microsoft.com y para los puntos de conexión del servidor cuando se reinicie Visual Studio.

    O

- Si desea usar las credenciales predeterminadas con el proxy, puede realizar las acciones siguientes:

  1. Busque **devenv.exe.config** (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Archivos de programa (x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#>" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Debe insertar la dirección correcta del proxy de la red en `proxyaddress="<http://<yourproxy:port#>`.

     O

- También puede seguir las instrucciones que aparecen en la entrada de blog [How to connect through an authenticated Web Proxy](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) (Cómo conectarse a través de un proxy web autenticado), que muestra cómo agregar código que le permitirá usar el proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Error: La conexión subyacente está cerrada

Si usa Visual Studio en una red privada que tiene un firewall, es posible que Visual Studio no pueda conectarse a algunos recursos de red. Estos recursos pueden incluir Azure DevOps Services para el inicio de sesión y la concesión de licencias, NuGet y los servicios de Azure. Si se produce un error en Visual Studio al conectarse a uno de estos recursos, verá el mensaje de error siguiente:

  **Se ha terminado la conexión: An unexpected error occurred on send** (Se ha producido un error inesperado en el envío)

Visual Studio usa el protocolo de Seguridad de la capa de transporte (TLS) 1.2 para conectarse a recursos de red. Los dispositivos de seguridad de algunas redes privadas bloquean ciertas conexiones de servidor cuando Visual Studio usa TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Para corregir este error de conexión

Habilite las conexiones para las direcciones URL siguientes:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (para las conexiones de Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (hospeda contenido de la red de entrega de contenido, o red CDN)

- &#42;.gallerycdn.vsassets.io (hospeda extensiones de Azure DevOps Services)

- static2.sharepointonline.com (hospeda los recursos que Visual Studio usa en el kit de tejido interfaz de la usuario de Office, como las fuentes)

- &#42.nuget.org (para las conexiones de NuGet)

  > [!NOTE]
  > Es posible que las direcciones URL de servidores NuGet privados no se incluyan en la lista. Puede buscar los servidores NuGet que se utilizan en %APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación y uso de Visual Studio detrás de un firewall o servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Instalación de Visual Studio 2017](install-visual-studio.md)
