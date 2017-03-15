---
title: "Error: No se puede iniciar la depuraci&#243;n en el servidor Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, errores de aplicación Web"
  - "depurar [Visual Studio], errores"
  - "depurar aplicaciones web ASP.NET, no se puede iniciar la depuración (error)"
  - "errores [depurador], no se puede iniciar la depuración"
  - "servidores HTTP, error de depuración"
  - "IIS, depurar las DLL"
  - "depuración remota, errores"
  - "seguridad [depurador], aplicaciones web"
  - "configuración de seguridad, comprobar los sitios Web predeterminados"
  - "no se puede iniciar la depuración (error)"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: No se puede iniciar la depuraci&#243;n en el servidor Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se intenta depurar una aplicación de ASP.NET que se ejecuta en un servidor web, puede obtener este mensaje de error: No se puede iniciar la depuración en el servidor Web.  
  
 En la mayoría de los casos, este error se produce porque IIS no está configurado correctamente.  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> Asegúrese de que IIS está correctamente configurado  
 Para obtener información acerca de la implementación en IIS 8 con una aplicación de MVC 5, consulte [Publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Para obtener información sobre la implementación de IIS7.5, consulte [Depuración ASP.NET remota en un equipo remoto de IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Asegúrese de que las Herramientas remotas de Visual Studio están instaladas  
 Si está intentando depurar en un servidor web remoto, debe instalar las Herramientas remotas de Visual Studio. Para obtener información sobre cómo descargar e instalar las herramientas remotas, vea [Depuración remota](../debugger/remote-debugging.md).  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> Asegúrese de que ASP.NET está instalado  
 **IIS 8**  
  
 Para IIS 8, se instala ASP.NET como parte de IIS.  
  
1.  En **Administrador del servidor**, seleccione**Panel** y haga clic en **Agregar roles y características**.  
  
2.  En la página **Tipo de instalación**, seleccione **Instalación basada en características o en roles** y haga clic en **Siguiente**.  
  
3.  En la página **Seleccionar servidor de destino**, elija **Seleccionar un servidor del grupo de servidores**, seleccione el servidor y haga clic en **Siguiente**.  
  
4.  En el **Seleccionar roles del servidor** seleccione **Servidor web \(IIS\)** y haga clic en **Siguiente**.  
  
5.  En la **página Seleccionar características**, haga clic en **Siguiente**.  
  
6.  En la página **Rol de servidor web \(IIS\)** haga clic en **Siguiente**.  
  
7.  En la página **Seleccionar servicios de rol**, tenga en cuenta los servicios de rol preseleccionados que se instalan de forma predeterminada, expanda el nodo **Servidor de aplicaciones** y el nodo **.NET Framework 4.5** y, a continuación, seleccione **ASP.NET 4.5**. \(Si instaló .NET 3.5, seleccione **ASP.NET 3.5** también.\)  
  
8.  En la página **Confirmar selecciones de instalación**, elija **Instalar**.  
  
9. En la página **Progreso de la instalación**, confirme que la instalación del rol de servidor web \(IIS\) y los servicios de rol requeridos se completaron correctamente y, luego, haga clic en **Cerrar**.  
  
 **IIS 7.5 y versiones anteriores**  
  
 Para IIS 7.5 y versiones anteriores, desde una ventana del símbolo del sistema, ejecute el siguiente comando:  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## Solucionar problemas básicos  
 Estas son algunas acciones que puede realizar para asegurarse de que la aplicación ASP.NET se implemente correctamente.  
  
## Abrir la página de localhost en el explorador  
 Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.  
  
## Abrir la página de localhost en el explorador  
 Inicie un explorador web y escriba la dirección URL de la página que está intentando depurar \(por ejemplo: `http://localhost/MyWebApplication`\). Si IIS no está configurado correctamente o no se implementó correctamente la aplicación ASP.NET, debería obtener errores que le ayudarán a corregir la configuración IIS y la implementación de ASP.NET.  
  
## Crear una aplicación ASP.NET básica en el servidor  
 Intente crear una aplicación ASP.NET básica local en el servidor e intente depurarla.  
  
## Resolver errores de autenticación si solo usa la dirección IP  
 La depuración de un servidor Web requiere la autenticación NTLM. De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Para corregir este problema, puede especificar el nombre del equipo remoto,  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> Asociar manualmente al proceso  
 Si sigue recibiendo un mensaje de error al iniciar la depuración, puede intentar depurar la aplicación mediante una asociación manual.  
  
-   Inicie la aplicación sin depuración. \(En el menú **Depurar**, elija **Iniciar sin depurar**.\)  
  
-   Haga clic en **Depurar \/ Asociar al proceso**.  Cuando aparezca la ventana, habilite **Mostrar procesos de todos los usuarios**.  
  
-   Busque el proceso adecuado y asócielo al depurador. Para las aplicaciones ASP.NET anteriores a MVC 5, el proceso es w3wp.exe. Para MVC 5, vea [Publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)