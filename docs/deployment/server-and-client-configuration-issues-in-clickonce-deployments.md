---
title: Servidor y problemas de configuración de cliente en implementaciones de ClickOnce | Documentos de Microsoft
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
ms.openlocfilehash: 077333237d1b384208355be7edb1aeb184678a05
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemas de configuración de servidor y cliente en implementaciones de ClickOnce
Si utiliza Internet Information Services (IIS) en Windows Server, y la implementación contiene un tipo de archivo que Windows no reconoce, como un archivo de Microsoft Word, IIS no transmitirá dicho archivo y no se realizará correctamente la implementación.  
  
 Además, algunos servidores Web y Web como aplicación de software, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contienen una lista de archivos y tipos de archivo que no se puede descargar. Por ejemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] evita la descarga de todos los archivos Web.config. Estos archivos pueden contener información confidencial, como nombres de usuario y contraseñas.  
  
 Aunque esta restricción no debería causar problemas para descargar core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos, como manifiestos y ensamblados, esta restricción puede impedir la descarga archivos de datos incluidos como parte de su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. En [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puede resolver este error quitando el controlador que impide la descarga de estos archivos desde el Administrador de configuración de IIS. Consulte la documentación del servidor IIS para obtener más detalles.  
  
 Algunos servidores Web podrían bloquear los archivos con extensiones como .dll y .config, .mdf. Las aplicaciones basadas en Windows normalmente incluyen archivos con algunas de estas extensiones. Si un usuario intenta ejecutar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] una aplicación que tiene acceso a un archivo bloqueado en un servidor Web, se producirá un error. En lugar de desbloquear todas las extensiones de archivo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publica cada archivo de aplicación con una extensión de archivo ".deploy" de forma predeterminada. Por lo tanto, solo el administrador debe configurar el servidor Web para desbloquear las siguientes extensiones de archivo de tres:  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Sin embargo, puede deshabilitar esta opción desactivando la **usar la extensión de archivo ".deploy"** opción el [Publish Options Dialog Box](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), en cuyo caso debe configurar el servidor Web para desbloquear todas las extensiones de archivo se utiliza en la aplicación.  
  
 Tendrá que configurar .manifest, Application y .deploy, por ejemplo, si está utilizando IIS donde no ha instalado el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o si está utilizando otro servidor Web (por ejemplo, Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce y capa de Sockets seguros (SSL)  
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación funcionará sin problemas a través de SSL, excepto cuando Internet Explorer genera un mensaje sobre el certificado SSL. El símbolo del sistema puede generarse cuando se produce algún error con el certificado, como cuando no coinciden los nombres de sitio o el certificado ha expirado. Para realizar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funcione a través de una conexión SSL, asegúrese de que el certificado está actualizado, y que los datos del certificado coincide con los datos del sitio.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce y autenticación de Proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona compatibilidad para la autenticación integrada de Windows de proxy a partir de .NET Framework 3.5. No se requiere ninguna directiva machine.config concreta. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no proporciona soporte técnico para otros protocolos de autenticación como básica o implícita.  
  
 También puede aplicar una revisión a .NET Framework 2.0 para habilitar esta característica. Para obtener más información, consulta http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Para obtener más información, consulte [ \<defaultProxy > Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce y compatibilidad con el explorador Web  
 Actualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las instalaciones se iniciarán solo si la dirección URL para el manifiesto de implementación se abre mediante Internet Explorer. Una implementación cuya dirección URL se inicia desde otra aplicación, como Microsoft Office Outlook, se iniciará correctamente sólo si Internet Explorer está configurado como el explorador Web predeterminado.  
  
> [!NOTE]
>  Mozilla Firefox se admite si el proveedor de implementación no está en blanco o la extensión de Asistente de Microsoft .NET Framework está instalada. Esta extensión se incluye con .NET Framework 3.5 SP1. Para obtener soporte XBAP, el complemento NPWPF cuando sea necesario.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Activar las aplicaciones ClickOnce a través de Scripting del explorador  
 Si ha desarrollado una página Web personalizada que inicia un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación utilizando Active Scripting, es posible que la aplicación no se iniciará en algunos equipos. Internet Explorer contiene una configuración denominada **Preguntar automáticamente para descargas de archivos**, lo cual afecta a este comportamiento. Esta opción está disponible en la **seguridad** ficha su **opciones** menú que afecta a este comportamiento. Se llama **Preguntar automáticamente para descargas de archivos**, y se muestra debajo de la **descarga** categoría. La propiedad se establece en **habilitar** de forma predeterminada para páginas Web de la intranet y a **deshabilitar** de forma predeterminada para las páginas Web de Internet. Cuando esta opción está establecida en **deshabilitar**, cualquier intento activar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante programación (por ejemplo, asignando su dirección URL para el `document.location` propiedad) se bloquearán. En este caso, los usuarios pueden iniciar aplicaciones solo a través de una descarga iniciada por el usuario, por ejemplo, haciendo clic en un hipervínculo que se establece en dirección URL de la aplicación.  
  
## <a name="additional-server-configuration-issues"></a>Problemas de configuración de servidor adicionales  
  
##### <a name="administrator-permissions-required"></a>Permisos de administrador necesarios  
 Debe tener permisos de administrador en el servidor de destino si está publicando con HTTP. IIS requiere este nivel de permisos. Si no va a publicar mediante HTTP, sólo necesita escribir permisos en la ruta de acceso de destino.  
  
##### <a name="server-authentication-issues"></a>Problemas de autenticación de servidor  
 Al publicar en un servidor remoto con "Acceso anónimo" desactivado, recibirá la advertencia siguiente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Puede hacer que la autenticación NTLM (NT desafío / respuesta) funcione si el sitio solicita credenciales distintas de las credenciales predeterminadas y, en el cuadro de diálogo seguridad haga clic en **Aceptar** cuando se le pregunte si desea guardar proporcionado credenciales para sesiones futuras. Sin embargo, esta solución no funcionará para la autenticación básica.  
  
## <a name="using-third-party-web-servers"></a>Con los servidores Web de terceros  
 Si está implementando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación desde un servidor Web que no sean IIS, puede experimentar un problema si el servidor devuelve el tipo de contenido incorrecto para la clave [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos, como el manifiesto de implementación y el manifiesto de aplicación. Para resolver este problema, consulte la Ayuda de su servidor Web documentación sobre cómo agregar nuevos tipos de contenido al servidor y asegúrese de que todas las asignaciones de extensión de nombre de archivo aparecen en la siguiente tabla están en vigor.  
  
|Extensión de nombre de archivo|Tipo de contenido|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce y unidades asignadas  
 Si usa Visual Studio para publicar una aplicación ClickOnce, no puede especificar una unidad asignada como la ubicación de instalación. Sin embargo, puede modificar la aplicación ClickOnce para instalar desde una unidad asignada mediante el generador de manifiestos y el Editor (Mage.exe y MageUI.exe). Para obtener más información, consulte [Mage.exe (generación de manifiestos y herramienta de edición)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) y [MageUI.exe (generación de manifiestos y herramienta de edición, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>No se admite el protocolo FTP para instalar aplicaciones  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite la instalación de aplicaciones desde cualquier servidor Web HTTP 1.1 o servidor de archivos. FTP, el protocolo de transferencia de archivos, no se admite para la instalación de aplicaciones. Puede usar FTP para publicar aplicaciones. En la tabla siguiente se resume estas diferencias:  
  
|Tipo de dirección URL|Descripción|  
|--------------|-----------------|  
|FTP: / /|Puede publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo.|  
|http://|Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo.|  
|https://|Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo.|  
|File://|Puede instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante este protocolo.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Firewall de Windows  
 De forma predeterminada, Windows XP SP2 habilita el Firewall de Windows. Si está desarrollando la aplicación en un equipo que tiene instalado Windows XP, está todavía puede publicar y ejecutar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones desde el servidor local que se ejecuta IIS. Sin embargo, no se puede tener acceso a ese servidor que está ejecutando IIS desde otro equipo a menos que abra el Firewall de Windows. Para obtener instrucciones acerca de cómo administrar el Firewall de Windows, consulte la Ayuda de Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Habilitar las extensiones de servidor de FrontPage  
 Extensiones de servidor de FrontPage de Microsoft es necesaria para la publicación de aplicaciones en un servidor Web de Windows que utiliza HTTP.  
  
 De forma predeterminada, Windows Server no tiene instaladas extensiones de servidor de FrontPage. Si desea usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para publicar en un servidor Web de Windows Server que utilice HTTP con las extensiones de servidor de FrontPage, debe instalar primero las extensiones de servidor de FrontPage. Puede realizar la instalación mediante la herramienta de administración Administre su servidor en Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Tipos de contenido bloqueado  
 IIS en [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloqueos abajo todos los tipos de archivo excepto para determinados tipos de contenido conocidos (por ejemplo, .htm, .html, .txt y así sucesivamente). Para habilitar la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones que utilizan este servidor, debe cambiar la configuración de IIS para permitir la descarga de archivos de tipo Application Manifest y cualquier otro tipo de archivo personalizado utilizado por la aplicación.  
  
 Si implementa mediante un servidor IIS, ejecute inetmgr.exe y agregue nuevos tipos de archivo para la página Web predeterminada:  
  
-   Para las extensiones de Application y .manifest, el tipo MIME debe ser "application/x-ms-application". Para otros tipos de archivo, el tipo MIME debe ser "application/octet-stream".  
  
-   Si crea un tipo MIME con extensión "*" y el tipo MIME "application/octet-stream", permitirá que los archivos de tipo de archivo desbloqueado para descargarse. (Sin embargo, bloquea los tipos como .aspx y .asmx no se puede descargar el archivo).  
  
 Para obtener instrucciones específicas acerca de cómo configurar tipos MIME en Windows Server, consulte el artículo de Microsoft Knowledge Base KB326965, "IIS 6.0 Does no sirve tipos desconocidos MIME" en [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Asignaciones de tipo de contenido  
 Cuando se publica a través de HTTP, el tipo de contenido (también conocido como tipo MIME) para el archivo Application debe ser "application/x-ms-application". Si tiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] instalado en el servidor, se establecerá automáticamente automáticamente. Si esto no está instalado, debe crear una asociación de tipo MIME para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación vroot (o todo el servidor).  
  
 Si implementa mediante un servidor IIS, ejecute inetmgr.exe y agregue un nuevo tipo de contenido de "application/x-ms-application" para la extensión de Application.  
  
## <a name="http-compression-issues"></a>Problemas de compresión HTTP  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], podrá realizar descargas que utilicen la compresión HTTP, una tecnología de servidor Web que utiliza el algoritmo GZIP para comprimir un flujo de datos antes de enviar la secuencia al cliente. El cliente, en este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], descomprime la secuencia antes de leer los archivos.  
  
 Si está utilizando IIS, puede habilitar fácilmente la compresión HTTP. Sin embargo, cuando se habilita la compresión HTTP, sólo está habilitada para determinados tipos de archivo, es decir, los archivos HTML y texto. Para habilitar la compresión de ensamblados (.dll), XML (.xml), manifiestos de implementación (Application) y manifiestos de aplicación (.manifest), debe agregar estos tipos de archivo a la lista de tipos de IIS que se comprima. Hasta que agregue los tipos de archivo a la implementación, se comprimirá sólo archivos de texto y HTML.  
  
 Para obtener instrucciones detalladas para IIS, consulte [cómo especificar tipos de documento adicionales para la compresión HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)