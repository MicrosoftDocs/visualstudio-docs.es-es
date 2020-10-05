---
title: Solución de problemas de errores de proxy o de red
description: Busque soluciones para los errores relacionados con la red o con el proxy que puede experimentar al instalar o usar Visual Studio detrás de un firewall o un servidor proxy.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0abe51b9f01d0c1f380c4762a7d0d4f457964aa7
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135136"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio

Tenemos soluciones para la mayoría de los errores típicos relacionados con la red o con el proxy que puede encontrar cuando instala o usa Visual Studio detrás de un firewall o un servidor proxy.

## <a name="error-proxy-authorization-required"></a>Error: "Se necesita autorización de proxy"

Por lo general, este error se produce cuando los usuarios están conectados a Internet a través de un servidor proxy y este bloquea las llamadas que hace Visual Studio a algunos recursos de red.

### <a name="to-fix-this-proxy-error"></a>Para corregir este error de proxy

- Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales cuando se le solicite en el cuadro de diálogo.

- Si el reinicio de Visual Studio no soluciona el problema, es posible que el servidor proxy no pida credenciales para direcciones http:&#47;&#47;go.microsoft.com pero sí para direcciones &#42;.visualStudio.microsoft.com. Para estos servidores, considere la posibilidad de agregar las siguientes direcciones URL a una lista de permitidas a fin de desbloquear todos los escenarios de inicio de sesión en Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Si no, puede quitar la dirección http:&#47;&#47;go.microsoft.com de la lista de permitidas para que el cuadro de diálogo de autenticación de proxy aparezca para la dirección http:&#47;&#47;go.microsoft.com y para los puntos de conexión del servidor cuando se reinicie Visual Studio.

  O BIEN

- Si desea usar las credenciales predeterminadas con el proxy, puede realizar las acciones siguientes:

::: moniker range="vs-2017"

  1. Busque **devenv.exe.config** (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Archivos de programa (x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Debe insertar la dirección correcta del proxy de la red en `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Para obtener más información, vea las páginas [&lt;defaultProxy&gt; Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) (Elemento defaultProxy [Configuración de red]) y [&lt;proxy&gt; Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) (Elemento proxy [Configuración de red]).

::: moniker-end

::: moniker range="vs-2019"

  1. Busque **devenv.exe.config** (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** o **%Archivos de programa (x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Debe insertar la dirección correcta del proxy de la red en `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Para obtener más información, vea las páginas [&lt;defaultProxy&gt; Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) (Elemento defaultProxy [Configuración de red]) y [&lt;proxy&gt; Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) (Elemento proxy [Configuración de red]).

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Error: "Desconectado de Visual Studio" al intentar notificar un problema

Por lo general, este error se produce cuando un usuario está conectado a Internet a través de un servidor proxy y este bloquea las llamadas que hace Visual Studio a algunos recursos de red.

### <a name="to-fix-this-proxy-error"></a>Para corregir este error de proxy

1. Busque **feedback.exe.config** (el archivo de configuración feedback.exe) en: **%ProgramFiles(x86)%\Microsoft Visual Studio\Installer** o **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. En el archivo de configuración, compruebe si el siguiente código está presente; si el código no está presente, agréguelo antes de la última línea de `</configuration>`.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

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

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (hospeda contenido de la red de entrega de contenido, o red CDN)

- &#42;.gallerycdn.vsassets.io (hospeda extensiones de Azure DevOps Services)

- static2.sharepointonline.com (hospeda los recursos que Visual Studio usa en el kit de tejido interfaz de la usuario de Office, como las fuentes)

- &#42;.nuget.org (para las conexiones de NuGet)

  > [!NOTE]
  > Es posible que las direcciones URL de servidores NuGet privados no se incluyan en la lista. Puede buscar los servidores NuGet que se utilizan en %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Error: "No se pudo analizar el identificador de un proceso primario"

Es posible que encuentre este mensaje de error al usar un programa previo de Visual Studio y un archivo response.json en una unidad de red. El origen del error es el control de cuentas de usuario (UAC) de Windows.

Este error se puede producir por este motivo: una unidad de red asignada o un recurso compartido de [UNC](/dotnet/standard/io/file-path-formats#unc-paths) está vinculado al token de acceso de un usuario. Cuando se habilita UAC, se crean dos [tokens de acceso](/windows/win32/secauthz/access-tokens) de usuario: uno *con* acceso de administrador y otro *sin* acceso de administrador. Cuando se crea una unidad de red o el recurso compartido, el token de acceso actual del usuario está vinculado a él. Como el programa previo se debe ejecutar como administrador, no podrá acceder a la unidad de red o al recurso compartido si la unidad o el recurso compartido no están vinculados a un token de acceso de usuario con acceso de administrador.

### <a name="to-fix-this-error"></a>Para corregir este error

Puede usar el comando `net use` o cambiar la configuración de directiva de grupo de UAC. Para más información sobre estas soluciones alternativas y cómo implementarlas, vea los siguientes artículos de soporte técnico de Microsoft:

* [Las unidades asignadas no están disponibles desde un símbolo del sistema con privilegios elevados si UAC está configurado para "Solicitar credenciales" en Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Es posible que los programas no puedan acceder a algunas ubicaciones de red después de activar el Control de cuentas de usuario en sistemas operativos Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte también

* [Instalar y usar Visual Studio detrás de un firewall o servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Instalación de Visual Studio](install-visual-studio.md)
