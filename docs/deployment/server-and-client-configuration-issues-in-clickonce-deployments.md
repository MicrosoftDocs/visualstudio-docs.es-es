---
title: Problemas de configuración de cliente y servidor (ClickOnce)
description: Obtenga información sobre los problemas de configuración de cliente y servidor que pueden afectar a la implementación de la aplicación ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f0361816d0621f52e9f95f4159dd0d46f4f5951
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352012"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemas de configuración de servidor y cliente en implementaciones de ClickOnce
Si usa Internet Information Services (IIS) en Windows Server y la implementación contiene un tipo de archivo que Windows no reconoce, como un archivo de Microsoft Word, IIS rechazará transmitir ese archivo y la implementación no se realizará correctamente.

 Además, algunos servidores web y software de aplicación web, como , contienen una lista de archivos y tipos de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] archivo que no se pueden descargar. Por ejemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impide la descarga de todos los *Web.config* archivos. Estos archivos pueden contener información confidencial, como nombres de usuario y contraseñas.

 Aunque esta restricción no debería causar problemas para descargar archivos principales, como manifiestos y ensamblados, esta restricción puede impedir que descargue los archivos de datos incluidos como parte de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. En , puede resolver este error quitando el controlador que prohíbe la descarga de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] estos archivos desde el administrador de configuración de IIS. Consulte la documentación del servidor IIS para obtener más detalles.

 Algunos servidores web pueden bloquear archivos con extensiones como *.dll*, *.config* y *.mdf*. Las aplicaciones basadas en Windows suelen incluir archivos con algunas de estas extensiones. Si un usuario intenta ejecutar una aplicación que tiene acceso a un archivo bloqueado en un servidor web, se producirá [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un error. En lugar de desbloquear todas las extensiones de archivo, publica todos los archivos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación con una extensión de archivo *.deploy* de forma predeterminada. Por lo tanto, el administrador solo necesita configurar el servidor web para desbloquear las tres extensiones de archivo siguientes:

- *.application*

- *.manifest*

- *.deploy*

  Sin embargo, puede deshabilitar esta opción desactivando la opción Usar extensión de archivo **".deploy"** en el cuadro de diálogo Opciones de publicación [,](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))en cuyo caso debe configurar el servidor web para desbloquear todas las extensiones de archivo usadas en la aplicación.

  Tendrá que configurar *.manifest,* *.application* y *.deploy,* por ejemplo, si usa IIS donde no ha instalado el .NET Framework o si usa otro servidor web (por ejemplo, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce y Capa de sockets seguros (SSL)
 Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación funcionará correctamente sobre SSL, excepto Internet Explorer genera una pregunta sobre el certificado SSL. El mensaje se puede generar cuando hay algún problema con el certificado, por ejemplo, cuando los nombres de sitio no coinciden o el certificado ha expirado. Para realizar el trabajo a través de una conexión SSL, asegúrese de que el certificado está actualizado y de que los datos del certificado coinciden con los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] datos del sitio.

## <a name="clickonce-and-proxy-authentication"></a>Autenticación de ClickOnce y proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona compatibilidad con la autenticación de proxy integrada de Windows a partir .NET Framework 3.5. No se machine.config directivas específicas. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no proporciona compatibilidad con otros protocolos de autenticación como Basic o Digest.

 También puede aplicar una revisión a .NET Framework 2.0 para habilitar esta característica. Para obtener más información, vea [FIX: Error message when you try to install a ClickOnce application that you created in the .NET Framework 2.0 on a client computer that is configured to use a proxy server: "Proxy authentication required"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)(Corrección: mensaje de error al intentar instalar una aplicación ClickOnce que creó en .NET Framework 2.0 en un equipo cliente configurado para usar un servidor proxy): "Se requiere autenticación de proxy".

 Para obtener más información, [ \<defaultProxy> vea elemento (configuración de red).](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)

## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilidad de ClickOnce y explorador web
 Actualmente, las instalaciones solo se iniciarán si la dirección URL del manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se abre mediante Internet Explorer. Una implementación cuya dirección URL se inicia desde otra aplicación, como Microsoft Office Outlook, se iniciará correctamente solo si Internet Explorer se establece como explorador web predeterminado.

> [!NOTE]
> Mozilla Firefox es compatible si el proveedor de implementación no está en blanco o si la Microsoft .NET Framework Assistant está instalada. Esta extensión se empaqueta con .NET Framework 3.5 SP1. Para la compatibilidad con XBAP, el complemento NPWPF se activa cuando es necesario.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Activación de aplicaciones ClickOnce mediante scripting de explorador
 Si ha desarrollado una página web personalizada que inicia una aplicación mediante scripting activo, es posible que la aplicación no se inicie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en algunas máquinas. Internet Explorer contiene una configuración denominada Solicitud automática de descargas **de archivos,** lo que afecta a este comportamiento. Esta configuración está disponible en la **pestaña Seguridad** de su **menú** Opciones que afecta a este comportamiento. Se denomina **Automatic prompting for file downloads**(Solicitud automática de descargas de archivos) y aparece debajo de la **categoría** Descargas. La propiedad se establece en **Habilitar de** forma predeterminada para páginas web de intranet y **en** Deshabilitar de forma predeterminada para páginas web de Internet. Cuando esta opción se establece en **Deshabilitar**, se bloqueará cualquier intento de activar una aplicación mediante programación (por ejemplo, asignando su dirección URL a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la propiedad `document.location` ). En esta circunstancia, los usuarios solo pueden iniciar aplicaciones a través de una descarga iniciada por el usuario, por ejemplo, haciendo clic en un hipervínculo establecido en la dirección URL de la aplicación.

## <a name="additional-server-configuration-issues"></a>Problemas adicionales de configuración del servidor

##### <a name="administrator-permissions-required"></a>Permisos de administrador necesarios
 Debe tener permisos de administrador en el servidor de destino si va a publicar con HTTP. IIS requiere este nivel de permisos. Si no va a publicar con HTTP, solo necesita permiso de escritura en la ruta de acceso de destino.

##### <a name="server-authentication-issues"></a>Problemas de autenticación del servidor
 Cuando publique en un servidor remoto que tenga desactivado "Acceso anónimo", recibirá la siguiente advertencia:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Puede hacer que la autenticación NTLM (nt challenge-response) funcione si el sitio solicita credenciales que  no sean las predeterminadas y, en el cuadro de diálogo de seguridad, haga clic en Aceptar cuando se le pida si desea guardar las credenciales proporcionadas para sesiones futuras. Sin embargo, esta solución alternativa no funcionará para la autenticación básica.

## <a name="use-third-party-web-servers"></a>Uso de servidores web de terceros
 Si va a implementar una aplicación desde un servidor web distinto de IIS, puede experimentar un problema si el servidor devuelve el tipo de contenido incorrecto para los archivos de clave, como el manifiesto de implementación y el manifiesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de aplicación. Para resolver este problema, consulte la documentación de ayuda del servidor web sobre cómo agregar nuevos tipos de contenido al servidor y asegúrese de que todas las asignaciones de extensiones de nombre de archivo enumeradas en la tabla siguiente están en su lugar.

|Extensión de nombre de archivo|Tipo de contenido|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce y unidades asignadas
 Si usa Visual Studio para publicar una aplicación ClickOnce, no puede especificar una unidad asignada como ubicación de instalación. Sin embargo, puede modificar la aplicación ClickOnce para instalarla desde una unidad asignada mediante el Generador de manifiestos y el Editor (Mage.exe y MageUI.exe). Para obtener más información, [veaMage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) y [MageUI.exe (Herramienta de generación y edición de manifiestos, Cliente gráfico).](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocolo FTP no compatible para instalar aplicaciones
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite la instalación de aplicaciones desde cualquier servidor web HTTP 1.1 o servidor de archivos. FTP, el protocolo de transferencia de archivos, no se admite para instalar aplicaciones. Puede usar FTP solo para publicar aplicaciones. En la tabla siguiente se resumen estas diferencias:

| Tipo de dirección URL | Descripción |
|----------| - |
| ftp:// | Puede publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| http:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| https:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| file:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall
 De forma predeterminada, Windows XP SP2 habilita el Firewall de Windows. Si está desarrollando la aplicación en un equipo con Windows XP instalado, todavía puede publicar y ejecutar aplicaciones desde el servidor local que ejecuta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] IIS. Sin embargo, no puede acceder a ese servidor que ejecuta IIS desde otro equipo a menos que abra el Firewall de Windows. Consulte la Ayuda de Windows para obtener instrucciones sobre cómo administrar el Firewall de Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: habilitar extensiones de servidor FrontPage
 Extensiones de servidor de FrontPage de Microsoft es necesario para publicar aplicaciones en un servidor web de Windows que use HTTP.

 De forma predeterminada, Windows Server no tiene Extensiones de servidor de FrontPage instalado. Si desea usar para publicar en un servidor web de Windows Server que usa HTTP con Extensiones de servidor de FrontPage, primero debe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalar Extensiones de servidor de FrontPage. Puede realizar la instalación mediante la herramienta de administración Administrar el servidor en Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: tipos de contenido bloqueados
 IIS en bloquea todos los tipos de archivo excepto determinados tipos de contenido conocidos [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] (por ejemplo, *.htm*, *.html*, *.txt*, y así sucesivamente). Para habilitar la implementación de aplicaciones con este servidor, debe cambiar la configuración de IIS para permitir la descarga de archivos de tipo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *.application,* *.manifest* y cualquier otro tipo de archivo personalizado que use la aplicación.

 Si implementa con un servidor IIS, ejecute *inetmgr.exe* y agregue nuevos tipos de archivo para la página web predeterminada:

- Para las *extensiones .application* y *.manifest,* el tipo MIME debe ser "application/x-ms-application". Para otros tipos de archivo, el tipo MIME debe ser "application/octet-stream".

- Si crea un tipo MIME con la extensión " " y el tipo MIME "application/octet-stream", permitirá descargar los archivos de tipo de archivo \<em> desbloqueado. (Sin embargo, no se pueden descargar los tipos de archivo bloqueados, *\* como .aspx* y *\* .asmx).*

  Para obtener instrucciones específicas sobre cómo configurar tipos MIME en Windows Server, vea Cómo agregar un tipo [MIME a un sitio web o aplicación](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Asignaciones de tipos de contenido
 Al publicar a través de HTTP, el tipo de contenido (también conocido como tipo MIME) para el *archivo .application* debe ser "application/x-ms-application". Si tiene .NET Framework 2.0 instalado en el servidor, se establecerá automáticamente. Si no está instalado, debe crear una asociación de tipo MIME para la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vroot (o todo el servidor).

 Si implementa mediante un servidor IIS, ejecute <em>inetmgr.</em> exe y agregue un nuevo tipo de contenido de "application/x-ms-application" para la *extensión .application.*

## <a name="http-compression-issues"></a>Problemas de compresión HTTP
 Con , puede realizar descargas que usan la compresión HTTP, una tecnología de servidor web que usa el algoritmo GZIP para comprimir un flujo de datos antes de enviar la secuencia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] al cliente. En este caso, el cliente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] descomprime la secuencia antes de leer los archivos.

 Si usa IIS, puede habilitar fácilmente la compresión HTTP. Sin embargo, cuando se habilita la compresión HTTP, solo se habilita para determinados tipos de archivo, es decir, archivos HTML y de texto. Para habilitar la compresión para ensamblados (*.dll*), XML (*.xml*), manifiestos de implementación (*.application*) y manifiestos de aplicación (*.manifest*), debe agregar estos tipos de archivo a la lista de tipos para que IIS comprima. Hasta que agregue los tipos de archivo a la implementación, solo se comprimirán los archivos de texto y HTML.

 Para obtener instrucciones detalladas para IIS, [vea Cómo especificar tipos de documento adicionales para la compresión HTTP.](/troubleshoot/iis/content-types-http-compression)

## <a name="see-also"></a>Consulte también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)
