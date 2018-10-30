---
title: Servidor y problemas de configuración de cliente en implementaciones ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444cfa375fd4e2059ddf6458224836cdec6ff18f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849448"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemas de configuración de servidor y cliente en implementaciones ClickOnce
Si usa Internet Information Services (IIS) en Windows Server y la implementación contiene un tipo de archivo que Windows no reconocen, como un archivo de Microsoft Word, IIS no transmitirá dicho archivo y no se realizará correctamente la implementación.  

 Además, algunos servidores Web y Web como aplicación de software, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contienen una lista de archivos y tipos de archivo que no se puede descargar. Por ejemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] evita la descarga de todos los *Web.config* archivos. Estos archivos pueden contener información confidencial como nombres de usuario y contraseñas.  

 Aunque esta restricción no debería causar problemas para descargar core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos como ensamblados y manifiestos, esta restricción puede impedir la descarga archivos de datos incluidos como parte de su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. En [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puede resolver este error quitando el controlador que impide la descarga de estos archivos desde el Administrador de configuración de IIS. Consulte la documentación del servidor IIS para obtener más detalles.  

 Algunos servidores Web podrían bloquear los archivos con extensiones como *.dll*, *.config*, y *.mdf*. Las aplicaciones basadas en Windows normalmente incluyen archivos con algunas de estas extensiones. Si un usuario intenta ejecutar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que tiene acceso a un archivo bloqueado en un servidor Web, se producirá un error. En lugar de desbloquear todas las extensiones de archivo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publica cada archivo de aplicación con un *.deploy* extensión de archivo de forma predeterminada. Por lo tanto, solo el administrador debe configurar el servidor Web para desbloquear las siguientes extensiones de archivo de tres:  

- *.Application*  

- *manifest*  

- *Deploy* 

  Sin embargo, puede deshabilitar esta opción si desactiva la **usar extensión de archivo ".deploy"** opción el [Publish Options Dialog Box](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), en cuyo caso debe configurar el servidor Web para desbloquear todas las extensiones de archivo se usa en la aplicación.  

  Tendrá que configurar *.manifest*, *.application*, y *.deploy*, por ejemplo, si está utilizando IIS donde no haya instalado el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o si no está uso de otro servidor Web (por ejemplo, Apache).  

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce y la capa de Sockets seguros (SSL)  
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación funcionará bien a través de SSL, excepto cuando Internet Explorer envía un mensaje sobre el certificado SSL. El símbolo del sistema puede generarse cuando hay algún problema con el certificado, como cuando no coinciden los nombres de sitio o el certificado ha expirado. Para realizar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funcionan a través de una conexión SSL, asegúrese de que el certificado está actualizado y que los datos del certificado coincide con los datos del sitio.  

## <a name="clickonce-and-proxy-authentication"></a>Autenticación de proxy y ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona compatibilidad para la autenticación integrada de Windows de proxy a partir de .NET Framework 3.5. No se requiere ninguna directiva machine.config concreta. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no proporciona soporte técnico para otros protocolos de autenticación como básica o implícita.  

 También puede aplicar una revisión para .NET Framework 2.0 para habilitar esta característica. Para obtener más información, consulta http://go.microsoft.com/fwlink/?LinkId=158730.  

 Para obtener más información, consulte [ \<defaultProxy > (configuración de red) del elemento](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  

## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilidad del explorador Web y ClickOnce  
 Actualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalaciones se inician solo si la dirección URL para el manifiesto de implementación se abre mediante Internet Explorer. Una implementación cuya dirección URL se inicia desde otra aplicación, como Microsoft Office Outlook, se iniciará correctamente sólo si Internet Explorer está configurado como el explorador Web predeterminado.  

> [!NOTE]
>  Mozilla Firefox se admite si el proveedor de implementación no está en blanco o la extensión de Asistente de Microsoft .NET Framework está instalada. Esta extensión se empaqueta con .NET Framework 3.5 SP1. Para obtener soporte técnico de la aplicación XBAP, el complemento NPWPF cuando sea necesario.  

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Activar las aplicaciones ClickOnce mediante secuencias de comandos de explorador  
 Si ha desarrollado una página Web personalizada que se inicia un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación utilizando Active Scripting, es posible que la aplicación no se iniciará en algunos equipos. Internet Explorer contiene una configuración denominada **Preguntar automáticamente para descargas de archivo**, lo que afecta a este comportamiento. Esta opción está disponible en el **seguridad** pestaña su **opciones** menú que afecta a este comportamiento. Se llama **Preguntar automáticamente para descargas de archivo**, y se enumera bajo el **descargas** categoría. La propiedad está establecida en **habilitar** de forma predeterminada para las páginas Web de intranet y a **deshabilitar** de forma predeterminada para las páginas Web de Internet. Cuando esta opción se establece en **deshabilitar**, cualquier intento activar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante programación (por ejemplo, mediante la asignación de la dirección URL para el `document.location` propiedad) se bloquearán. En este caso, los usuarios pueden iniciar aplicaciones solo a través de una descarga iniciada por el usuario, por ejemplo, si hace clic en un hipervínculo que se establece en dirección URL de la aplicación.  

## <a name="additional-server-configuration-issues"></a>Problemas de configuración de servidor adicionales  

##### <a name="administrator-permissions-required"></a>Permisos de administrador necesarios  
 Debe tener permisos de administrador en el servidor de destino si va a publicar con HTTP. IIS requiere este nivel de permisos. Si no va a publicar mediante HTTP, sólo necesita escribir permisos en la ruta de acceso de destino.  

##### <a name="server-authentication-issues"></a>Problemas de autenticación de servidor  
 Al publicar en un servidor remoto con "Acceso anónimo" desactivado, recibirá la advertencia siguiente:  

```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  

> [!NOTE]
>  Puede realizar la autenticación NTLM (NT desafío / respuesta) funcionará si el sitio solicita credenciales distintas de las credenciales predeterminadas y, en el cuadro de diálogo seguridad haga clic en **Aceptar** cuando se le pregunte si desea guardar proporcionado credenciales para sesiones futuras. Sin embargo, esta solución no funcionará para la autenticación básica.  

## <a name="use-third-party-web-servers"></a>Usar servidores Web de terceros  
 Si está implementando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación desde un servidor Web que no sean IIS, puede experimentar un problema si el servidor devuelve el tipo de contenido incorrecto para la clave [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos, como el manifiesto de implementación y el manifiesto de aplicación. Para resolver este problema, consulte la Ayuda de su servidor Web documentación acerca de cómo agregar nuevos tipos de contenido al servidor y asegúrese de que todas las asignaciones de extensión de nombre de archivo que aparece en la tabla siguiente están en su lugar.  

|Extensión de nombre de archivo|Tipo de contenido|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  

## <a name="clickonce-and-mapped-drives"></a>ClickOnce y unidades asignadas  
 Si usa Visual Studio para publicar una aplicación ClickOnce, no se puede especificar una unidad asignada como la ubicación de instalación. Sin embargo, puede modificar la aplicación ClickOnce para instalar desde una unidad asignada mediante el generador de manifiestos y el Editor (Mage.exe y MageUI.exe). Para obtener más información, consulte [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) y [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocolo FTP no es compatible para la instalación de aplicaciones  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite la instalación de aplicaciones desde cualquier servidor Web HTTP 1.1 o un servidor de archivos. FTP, el protocolo de transferencia de archivos, no se admite para la instalación de aplicaciones. Puede usar FTP para publicar solo las aplicaciones. En la tabla siguiente se resume estas diferencias:  


| Tipo de dirección URL | Descripción |
|----------| - |
| FTP: / / | Puede publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| http:// | Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| https:// | Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |
| File:// | Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Firewall de Windows  
 De forma predeterminada, Windows XP Service Pack 2 habilita el Firewall de Windows. Si está desarrollando su aplicación en un equipo que tiene instalado de Windows XP, están todavía puede publicar y ejecutar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones desde el servidor local que ejecuta IIS. Sin embargo, no se puede acceder al servidor que ejecuta IIS desde otro equipo a menos que abra el Firewall de Windows. Para obtener instrucciones acerca de cómo administrar el Firewall de Windows, consulte la Ayuda de Windows.  

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Habilitar extensiones de servidor  
 Extensiones de servidor de FrontPage de Microsoft es necesaria para publicar aplicaciones en un servidor Web de Windows que utiliza HTTP.  

 De forma predeterminada, Windows Server no tiene instalado FrontPage Server Extensions. Si desea usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para publicar en un servidor Web de Windows Server que utiliza HTTP con las extensiones de servidor de FrontPage, debe instalar primero extensiones de servidor. Puede realizar la instalación mediante el uso de la herramienta de administración administrar el servidor en Windows Server.  

## <a name="windows-server-locked-down-content-types"></a>Windows Server: Tipos de contenido bloqueado  
 IIS en [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloquea todos los tipos de archivo salvo ciertos tipos de contenido conocidos (por ejemplo, *.htm*, *.html*, *.txt*, y así sucesivamente). Para habilitar la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones que usen este servidor, deberá cambiar la configuración de IIS para permitir la descarga de archivos de tipo *.application*, *.manifest*y otros tipos de archivo personalizados usado por la aplicación.  

 Si implementa mediante un servidor IIS, ejecute *inetmgr.exe* y agregar nuevos tipos de archivo para la página Web predeterminada:  

- Para el *.application* y *.manifest* extensiones, el tipo MIME debe ser "application/x-ms-application". Para otros tipos de archivo, el tipo MIME debe ser "application/octet-stream".  

- Si crea un tipo MIME con extensión "<em>" y el tipo MIME "application/octet-stream", permitirá que los archivos de tipo de archivo desbloqueado para descargarse. (Sin embargo, los archivos bloqueados como *.aspx</em> y *.asmx* no se puede descargar.)  

  Para obtener instrucciones específicas sobre cómo configurar tipos MIME en Windows Server, consulte el artículo de Microsoft Knowledge Base KB326965, "IIS 6.0 no sirve tipos MIME desconocidos" en [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  

## <a name="content-type-mappings"></a>Asignaciones de tipo de contenido  
 Cuando se publica a través de HTTP, el tipo de contenido (también conocido como el tipo MIME) para el *.application* archivo debe ser "application/x-ms-application". Si tiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] instalado en el servidor, se establecerá para automáticamente. Si esto no está instalado, deberá crear una asociación de tipo MIME para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación vroot (o todo el servidor).  

 Si implementa mediante un servidor IIS, ejecute <em>inetmgr.</em> exe y agregue un nuevo tipo de contenido de "application/x-ms-application" para el *.application* extensión.  

## <a name="http-compression-issues"></a>Problemas de compresión HTTP  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], podrá realizar descargas que utilicen la compresión HTTP, una tecnología de servidor Web que utiliza el algoritmo GZIP para comprimir un flujo de datos antes de enviar la secuencia al cliente. El cliente, en este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], descomprime la secuencia antes de leer los archivos.  

 Si está utilizando IIS, puede habilitar fácilmente la compresión HTTP. Sin embargo, cuando se habilita la compresión HTTP, está habilitada solo para determinados tipos de archivo, es decir, los archivos HTML y texto. Para habilitar la compresión de ensamblados (*.dll*), XML (*.xml*), los manifiestos de implementación (*.application*) y los manifiestos de aplicación (*.manifest*), debe agregar estos tipos a la lista de tipos de IIS comprimir de archivos. Hasta que agregue los tipos de archivo a la implementación, se comprimirá sólo archivos de texto y HTML.  

 Para obtener instrucciones detalladas, consulte [cómo especificar tipos de documento adicionales para la compresión HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  

## <a name="see-also"></a>Vea también  
 [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)