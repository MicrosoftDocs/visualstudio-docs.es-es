---
title: "Problemas de configuraci&#243;n de servidor y cliente en implementaciones de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, solucionar problemas"
  - "implementar aplicaciones, ClickOnce"
  - "solucionar problemas en implementaciones ClickOnce"
  - "aplicaciones Windows, implementaciones ClickOnce"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Problemas de configuraci&#243;n de servidor y cliente en implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si usa Internet Information Services \(IIS\) en Windows Server y la implementación contiene un tipo de archivo que Windows no reconoce, como un archivo de Microsoft Word, IIS no transmitirá dicho archivo y no se podrá completar la implementación.  
  
 Además, algunos servidores web y software de aplicaciones web, como [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contienen una lista de archivos y tipos de archivo que no puede descargar.  Por ejemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] evita la descarga de todos los archivos Web.config.  Estos archivos pueden contener información confidencial como nombres de usuario y contraseñas.  
  
 Aunque esta restricción no debería causar problemas para descargar archivos básicos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], como manifiestos y ensamblados, puede impedir la descarga de los archivos de datos incluidos como parte de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puede resolver este error quitando el controlador que impide la descarga de esos archivos del administrador de configuración de IIS.  Consulte la documentación del servidor IIS para obtener información más detallada.  
  
 Algunos servidores Web podrían bloquear los archivos con extensiones como .dll, .config y .mdf.  Las aplicaciones basadas en Windows normalmente incluyen archivos con algunas de estas extensiones.  Si el usuario intenta ejecutar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que tiene acceso a un archivo bloqueado en un servidor web, se producirá un error.  En lugar de desbloquear todas las extensiones de archivo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publica cada archivo de aplicación de manera predeterminada con la extensión de archivo ".deploy".  Por consiguiente, el administrador sólo necesita configurar el servidor Web para desbloquear las tres extensiones de archivo siguientes:  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Sin embargo, puede deshabilitar esta opción borrando la opción **Usar la extensión de archivo "deploy"** en el cuadro de diálogo [Publish Options Dialog Box](http://msdn.microsoft.com/es-es/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), en cuyo caso debe configurar el servidor Web para desbloquear todas las extensiones de archivo utilizadas en la aplicación.  
  
 Por ejemplo, tendrá que configurar .manifest, .application y .deploy si está utilizando IIS donde no se haya instalado [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o si está utilizando otro servidor web \(por ejemplo, Apache\).  
  
## ClickOnce y Capa de sockets seguros \(SSL\)  
 Una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funcionará eficazmente con SSL, excepto cuando Internet Explorer envía un mensaje acerca del certificado SSL.  El mensaje puede aparecer cuando el certificado contiene un error, como cuando los nombres de los sitios no coinciden o el certificado ha expirado.  Para que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funcione con una conexión SSL, asegúrese de que el certificado esté actualizado y que sus datos coincidan con los datos del sitio.  
  
## ClickOnce y autenticación proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona compatibilidad con la autenticación proxy integrada de Windows a partir de .NET Framework 3.5.  No se requiere ninguna directiva machine.config concreta.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no proporciona compatibilidad con otros protocolos de autenticación como la autenticación básica o implícita.  
  
 También puede aplicar una revisión a .NET Framework 2.0 para habilitar esta característica.  Para obtener más información, vea http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730.  
  
 Para obtener más información, vea [\<defaultProxy\> \(Elemento, Configuración de red\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md).  
  
## ClickOnce y compatibilidad con el explorador web  
 Actualmente, las instalaciones de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sólo se inician si la dirección URL del manifiesto de implementación se abre mediante Internet Explorer.  Una implementación cuya dirección URL se inicia de otra aplicación, como Microsoft Office Outlook, sólo se iniciará correctamente si se establece Internet Explorer como explorador web predeterminado.  
  
> [!NOTE]
>  Se admite Mozilla Firefox si el proveedor de implementación no está en blanco o si está instalada la extensión Microsoft .NET Framework Assistant.  Esta extensión se incluye con .NET Framework 3.5 SP1.  Para la compatibilidad con XBAP, se activará el complemento NPWPF cuando sea preciso.  
  
## Activar las aplicaciones ClickOnce a través de scripting del explorador  
 Si ha desarrollado una página web personalizada que inicia una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante scripting activos, es posible que la aplicación no se inicie en algunos equipos.  Internet Explorer contiene una configuración denominada **Preguntar automáticamente si se debe descargar un archivo**, que afecta a este comportamiento.  Este valor está disponible en la ficha **Seguridad** del menú **Opciones** que afecta a este comportamiento.  Se denomina **Preguntar automáticamente para descargas de archivo** y se encuentra en la categoría  **Descargas**.  La propiedad se establece de forma predeterminada en **Habilitar** para las páginas Web de la intranet y en **Deshabilitar** para las páginas Web de Internet.  Cuando se establece en **Deshabilitar**, se bloqueará cualquier intento de activar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante programación \(por ejemplo, asignando su dirección URL a la propiedad `document.location`\).  En estas circunstancias, los usuarios pueden iniciar las aplicaciones únicamente a través de una descarga iniciada por el usuario, por ejemplo, haciendo clic en un hipervínculo establecido en la dirección URL de la aplicación.  
  
## Problemas adicionales de configuración del servidor  
  
##### Se requieren permisos de administrador  
 Debe tener permisos de administrador en el servidor destino si está publicando con HTTP.  IIS requiere este nivel de permisos.  Si no está publicando con HTTP, sólo necesita permiso de escritura en la ruta de acceso de destino.  
  
##### Problemas de autenticación de servidor  
 Al publicar en un servidor remoto con "Acceso anónimo" desactivado, recibirá la advertencia siguiente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  La autenticación NTLM \(desafío\/respuesta de NT\) funcionará si el sitio solicita credenciales distintas de las predeterminadas y, en el cuadro de diálogo de seguridad, hace clic en **Aceptar** si desea guardar las credenciales proporcionadas para futuras sesiones.  Sin embargo, esta misma solución no funcionará para la autenticación básica.  
  
## Usar servidores Web de terceros  
 Si está implementando una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde un servidor web distinto de IIS, puede que surjan problemas si el servidor devuelve el tipo de contenido incorrecto para los archivos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] clave, como el manifiesto de implementación y el manifiesto de aplicación.  Para resolver este problema, consulte la documentación de la Ayuda del servidor Web sobre cómo agregar nuevos tipos de contenido al servidor y asegúrese de que todas las asignaciones de extensión de nombre de archivo que se muestran en la siguiente tabla estén en su lugar.  
  
|Extensión de nombre de archivo|Tipo de contenido|  
|------------------------------------|-----------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce y unidades asignadas  
 Si utiliza Visual Studio para publicar una aplicación ClickOnce, no puede especificar una unidad asignada como ubicación de instalación.  Sin embargo, puede modificar la aplicación ClickOnce de modo que se instale desde una unidad asignada mediante el generador y el editor de manifiestos \(Mage.exe y MageUI.exe\).  Para obtener más información, vea [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) y [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
## No se admite el protocolo FTP para instalar aplicaciones  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite la instalación de aplicaciones desde cualquier servidor web HTTP 1.1 o servidor de archivos.  FTP, el protocolo de transferencia de archivos, no se admite para la instalación de aplicaciones.  Puede utilizar FTP para sólo publicar aplicaciones.  La tabla siguiente proporciona un resumen de estas diferencias.  
  
|Tipo de URL|Descripción|  
|-----------------|-----------------|  
|ftp:\/\/|Puede publicar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante este protocolo.|  
|http:\/\/|Puede instalar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante este protocolo.|  
|https:\/\/|Puede instalar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante este protocolo.|  
|file:\/\/|Puede instalar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante este protocolo.|  
  
## SP2 de Windows XP: Firewall de Windows  
 De manera predeterminada, SP2 de Windows XP habilita el Firewall de Windows.  Si está desarrollando su aplicación en un equipo con Windows XP instalado, todavía puede publicar y ejecutar las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde el servidor local que esté ejecutando IIS.  Sin embargo, no puede obtener acceso al servidor que está ejecutando IIS desde otro equipo, a menos que abra el Firewall de Windows.  Vea en la Ayuda de Windows las instrucciones para administrar Windows Firewall.  
  
## Windows Server: habilitar las Extensiones de servidor de FrontPage  
 Las Extensiones de servidor de FrontPage son necesarias para publicar aplicaciones en un servidor web de Windows que use HTTP.  
  
 De forma predeterminada, Windows Server no tiene instaladas las Extensiones de servidor de FrontPage.  Si desea usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para publicar en un servidor web de Windows Server que use HTTP con las Extensiones de servidor de FrontPage, deberá instalar primero las Extensiones de servidor de FrontPage.  Puede realizar la instalación mediante la herramienta de administración Administre su servidor de Windows Server.  
  
## Windows Server: tipos de contenido bloqueado  
 IIS en [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloquea todos los tipos de archivo salvo algunos tipos de contenido conocidos \(por ejemplo, .htm, .html, .txt, entre otros\).  Para habilitar la implementación de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante este servidor, hay que cambiar la configuración de IIS para permitir la descarga de archivos de tipo .application, .manifest y cualquier otro tipo de archivo personalizado utilizado por la aplicación.  
  
 Si implementa mediante un servidor IIS, ejecute inetmgr.exe y agregue nuevos Tipos de archivo para la página Web predeterminada:  
  
-   En el caso de las extensiones .application y .manifest, el tipo MIME debe ser "application\/x\-ms\-application". Para otros tipos de archivo, el tipo MIME debe ser "application\/octet\-stream".  
  
-   Si crea un tipo MIME con extensión "\*" y el tipo MIME es "application\/octet\-stream", podrá descargar archivos de tipo de archivo desbloqueado.  \(Sin embargo, no se pueden descargar tipos de archivo bloqueados como .aspx y .asmx.\)  
  
 Para obtener instrucciones concretas sobre la configuración de tipos MIME en Windows Server, vea el artículo de Microsoft Knowledge Base KB326965, "IIS 6.0 Does Not Serve Unknown MIME Types" at [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;es\-es;326965](http://support.microsoft.com/default.aspx?scid=kb;es-es;326965).  
  
## Asignaciones de tipo de contenido  
 Al publicar sobre HTTP, el tipo de contenido \(también conocido como tipo MIME\) para el archivo .application debe ser "application\/x\-ms\-application". Si tiene está instalado [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] en el servidor, el tipo se establecerá automáticamente.  Si no está instalado, hay que crear una asociación del tipo MIME para el vroot \(o todo el servidor\) de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Si implementa mediante un servidor IIS, ejecute inetmgr.exe y agregue un nuevo tipo de contenido de "application\/x\-ms\-application" para la extensión .application.  
  
## Problemas de compresión HTTP  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], podrá realizar descargas que utilicen la compresión HTTP, una tecnología de servidor web que utiliza el algoritmo GZIP para comprimir un flujo de datos antes de enviárselo al cliente.  El cliente, en este caso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], descomprime el flujo antes de leer los archivos.  
  
 Si está utilizando IIS, podrá habilitar la compresión HTTP con facilidad.  No obstante, cuando se habilita la compresión HTTP, sólo se habilita para determinados tipos de archivo, concretamente archivos HTML y archivos de texto.  Para habilitar la compresión de ensamblados \(.dll\), XML \(.xml\), manifiestos de implementación \(.application\) y manifiestos de aplicación \(.manifest\), debe agregar estos tipos de archivo a la lista de tipos de IIS que se pueden comprimir.  Hasta que agregue los tipos de archivo a la implementación, sólo se comprimirán archivos HTML y archivos de texto.  
  
 Para obtener instrucciones detalladas de IIS, vea [Cómo especificar tipos de documento adicionales para la compresión HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)