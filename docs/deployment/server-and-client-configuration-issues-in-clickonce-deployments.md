---
title: Problemas de configuración de servidor/cliente (ClickOnce)
description: Obtenga información acerca de los problemas de configuración de cliente y servidor que pueden afectar a la implementación de la aplicación ClickOnce.
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
ms.openlocfilehash: 469749c28acdb90e835082dd05010102ab50e52b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877621"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemas de configuración de servidor y cliente en implementaciones de ClickOnce
Si usa Internet Information Services (IIS) en Windows Server y la implementación contiene un tipo de archivo que Windows no reconoce, como un archivo de Microsoft Word, IIS rechazará la transmisión del archivo y la implementación no se realizará correctamente.

 Además, algunos servidores web y el software de aplicaciones Web, como [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , contienen una lista de archivos y tipos de archivo que no se pueden descargar. Por ejemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] evita la descarga de todos los archivos *Web.config* . Estos archivos pueden contener información confidencial, como nombres de usuario y contraseñas.

 Aunque esta restricción no debe causar problemas para descargar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos principales como manifiestos y ensamblados, esta restricción puede impedir la descarga de archivos de datos incluidos como parte de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. En [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , puede resolver este error quitando el controlador que prohíbe la descarga de estos archivos desde el administrador de configuración de IIS. Consulte la documentación del servidor IIS para obtener más detalles.

 Algunos servidores Web podrían bloquear archivos con extensiones como *. dll*, *. config* y *. MDF*. Las aplicaciones basadas en Windows suelen incluir archivos con algunas de estas extensiones. Si un usuario intenta ejecutar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que tiene acceso a un archivo bloqueado en un servidor Web, se producirá un error. En lugar de desbloquear todas las extensiones de archivo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publica todos los archivos de aplicación con una extensión de archivo *. deploy* de forma predeterminada. Por lo tanto, el administrador solo tiene que configurar el servidor web para desbloquear las tres extensiones de archivo siguientes:

- *. Application*

- *. manifest*

- *. deploy*

  Sin embargo, puede deshabilitar esta opción si desactiva la opción de **extensión de archivo ". deploy"** en el [cuadro de diálogo Opciones de publicación](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), en cuyo caso debe configurar el servidor web para desbloquear todas las extensiones de archivo usadas en la aplicación.

  Tendrá que configurar *. manifest*, *. Application* y *. deploy*, por ejemplo, si usa IIS donde no ha instalado el .NET Framework, o si está usando otro servidor Web (por ejemplo, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce y Capa de sockets seguros (SSL)
 Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación funcionará correctamente con SSL, excepto cuando Internet Explorer genere un mensaje sobre el certificado SSL. El mensaje puede producirse cuando hay algún problema con el certificado, por ejemplo, cuando los nombres de sitio no coinciden o el certificado ha expirado. Para hacer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] el trabajo a través de una conexión SSL, asegúrese de que el certificado esté actualizado y que los datos del certificado coincidan con los datos del sitio.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce y autenticación de proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona compatibilidad con la autenticación de proxy integrada de Windows a partir de .NET Framework 3,5. No se requieren directivas de machine.config específicas. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no proporciona compatibilidad con otros protocolos de autenticación como Basic o Digest.

 También puede aplicar una revisión a .NET Framework 2,0 para habilitar esta característica. Para obtener más información, consulte [corrección: mensaje de error al intentar instalar una aplicación ClickOnce creada en el .NET Framework 2,0 en un equipo cliente que está configurado para usar un servidor proxy: "se requiere autenticación proxy"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that).

 Para obtener más información, vea [ \<defaultProxy> elemento (configuración de red)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce y compatibilidad con exploradores Web
 Actualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las instalaciones solo se iniciarán si la dirección URL del manifiesto de implementación se abre con Internet Explorer. Una implementación cuya dirección URL se inicia desde otra aplicación, como Microsoft Office Outlook, se iniciará correctamente solo si Internet Explorer está establecido como el explorador Web predeterminado.

> [!NOTE]
> Mozilla Firefox es compatible Si el proveedor de implementación no está en blanco o si se ha instalado la extensión del asistente de Microsoft .NET Framework. Esta extensión está empaquetada con .NET Framework 3,5 SP1. En cuanto a la compatibilidad con XBAP, el complemento NPWPF se activa cuando sea necesario.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Activar aplicaciones ClickOnce a través de scripting del explorador
 Si ha desarrollado una página web personalizada que inicia una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante Active Scripting, es posible que la aplicación no se inicie en algunos equipos. Internet Explorer contiene una configuración denominada **solicitud automática de descargas de archivos**, lo que afecta a este comportamiento. Esta opción está disponible en la pestaña **seguridad** del menú **Opciones** que afecta a este comportamiento. Se denomina **solicitud automática de descargas de archivos** y aparece debajo de la categoría **descargas** . La propiedad se establece en **habilitado** de forma predeterminada para las páginas web de la intranet y para **deshabilitarla** de forma predeterminada para las páginas web de Internet. Cuando esta opción se establece en **Disable**, se bloqueará cualquier intento de activar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante programación (por ejemplo, mediante la asignación de su dirección URL a la `document.location` propiedad). En este caso, los usuarios pueden iniciar aplicaciones solo a través de una descarga iniciada por el usuario, por ejemplo, haciendo clic en un hipervínculo establecido en la dirección URL de la aplicación.

## <a name="additional-server-configuration-issues"></a>Problemas adicionales de configuración del servidor

##### <a name="administrator-permissions-required"></a>Permisos de administrador necesarios
 Debe tener permisos de administrador en el servidor de destino si va a publicar con HTTP. IIS requiere este nivel de permisos. Si no va a publicar mediante HTTP, solo necesitará el permiso de escritura en la ruta de acceso de destino.

##### <a name="server-authentication-issues"></a>Problemas de autenticación de servidor
 Al publicar en un servidor remoto que tiene desactivada la opción "acceso anónimo", recibirá la siguiente ADVERTENCIA:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Puede hacer que la autenticación NTLM (desafío-respuesta de NT) funcione si el sitio solicita credenciales distintas de las predeterminadas y, en el cuadro de diálogo seguridad, haga clic en **Aceptar** cuando se le pregunte si desea guardar las credenciales proporcionadas para futuras sesiones. Sin embargo, esta solución no funcionará para la autenticación básica.

## <a name="use-third-party-web-servers"></a>Usar servidores Web de terceros
 Si va a implementar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación desde un servidor Web distinto de IIS, puede experimentar un problema si el servidor devuelve el tipo de contenido incorrecto para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] los archivos de claves, como el manifiesto de implementación y el manifiesto de aplicación. Para resolver este problema, consulte la documentación de ayuda del servidor web sobre cómo agregar nuevos tipos de contenido al servidor y asegúrese de que todas las asignaciones de extensión de nombre de archivo que aparecen en la tabla siguiente están en su lugar.

|Extensión de nombre de archivo|Tipo de contenido|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce y unidades asignadas
 Si usa Visual Studio para publicar una aplicación ClickOnce, no puede especificar una unidad asignada como ubicación de instalación. Sin embargo, puede modificar la aplicación ClickOnce para instalarla desde una unidad asignada mediante el generador de manifiestos y el editor (Mage.exe y MageUI.exe). Para obtener más información, consulte [Mage.exe (herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) y [MageUI.exe (herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>No se admite el protocolo FTP para la instalación de aplicaciones
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite la instalación de aplicaciones desde cualquier servidor Web HTTP 1,1 o servidor de archivos. FTP, protocolo de transferencia de archivos, no se admite para la instalación de aplicaciones de. Puede usar FTP para publicar aplicaciones únicamente. En la tabla siguiente se resumen estas diferencias:

| Tipo de dirección URL | Descripción |
|----------| - |
| ftp:// | Puede publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| http:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| https:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| file:// | Puede instalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: firewall de Windows
 De forma predeterminada, Windows XP SP2 habilita el Firewall de Windows. Si va a desarrollar la aplicación en un equipo que tiene instalado Windows XP, todavía podrá publicar y ejecutar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones desde el servidor local que ejecuta IIS. Sin embargo, no se puede tener acceso a ese servidor en el que se ejecuta IIS desde otro equipo, a menos que se abra el Firewall de Windows. Consulte la ayuda de Windows para obtener instrucciones sobre la administración del firewall de Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: habilitar extensiones de servidor de FrontPage
 Extensiones de servidor de FrontPage de Microsoft es necesario para publicar aplicaciones en un servidor Web de Windows que utiliza HTTP.

 De forma predeterminada, Windows Server no tiene Extensiones de servidor de FrontPage instalado. Si desea usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para publicar en un servidor Web de Windows Server que usa http con extensiones de servidor de FrontPage, debe instalar extensiones de servidor de FrontPage primero. Puede realizar la instalación mediante la herramienta administrar la administración del servidor en Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: tipos de contenido bloqueados
 IIS de [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloquea todos los tipos de archivo excepto determinados tipos de contenido conocidos (por ejemplo, *. htm*, *. html*, *. txt*, etc.). Para habilitar la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones con este servidor, debe cambiar la configuración de IIS para permitir la descarga de archivos de tipo *. Application*, *. manifest* y cualquier otro tipo de archivo personalizado que use la aplicación.

 Si implementa mediante un servidor IIS, ejecute *inetmgr.exe* y agregue nuevos tipos de archivo para la página web predeterminada:

- En el caso de las extensiones *. Application* y *. manifest* , el tipo MIME debe ser "application/x-MS-Application". Para otros tipos de archivo, el tipo MIME debe ser "application/octet-stream".

- Si crea un tipo MIME con la extensión " \<em> " y el tipo MIME "application/octet-stream", permitirá que se descarguen los archivos de tipo de archivo desbloqueado. (Sin embargo, los tipos de archivos bloqueados como *\* . aspx* y *\* . asmx* no se pueden descargar).

  Para obtener instrucciones específicas sobre cómo configurar tipos MIME en Windows Server, consulte [Cómo agregar un tipo MIME a un sitio web o aplicación](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Asignaciones de tipos de contenido
 Al publicar a través de HTTP, el tipo de contenido (también conocido como tipo MIME) para el archivo *. Application* debe ser "application/x-MS-Application". Si tiene .NET Framework 2,0 instalado en el servidor, se establecerá automáticamente. Si no está instalado, debe crear una asociación de tipo MIME para la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación vroot (o todo el servidor).

 Si implementa mediante un servidor IIS, ejecute <em>inetmgr.</em> exe y agregue un nuevo tipo de contenido de "application/x-MS-Application" para la extensión *. Application* .

## <a name="http-compression-issues"></a>Problemas de compresión HTTP
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , puede realizar descargas que utilicen la compresión http, una tecnología de servidor Web que usa el algoritmo gzip para comprimir un flujo de datos antes de enviar la secuencia al cliente. El cliente (en este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ) descomprime la secuencia antes de leer los archivos.

 Si utiliza IIS, puede habilitar fácilmente la compresión HTTP. Sin embargo, cuando se habilita la compresión HTTP, solo se habilita para determinados tipos de archivo, es decir, archivos HTML y de texto. Para habilitar la compresión de ensamblados (*. dll*), XML (*. XML*), manifiestos de implementación (*. Application*) y manifiestos de aplicación (*. manifest*), debe agregar estos tipos de archivo a la lista de tipos para que IIS los comprima. Hasta que agregue los tipos de archivo a la implementación, solo se comprimirán los archivos de texto y HTML.

 Para obtener instrucciones detalladas para IIS, vea [Cómo especificar tipos de documentos adicionales para la compresión http](https://support.microsoft.com/help/234497).

## <a name="see-also"></a>Vea también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)
