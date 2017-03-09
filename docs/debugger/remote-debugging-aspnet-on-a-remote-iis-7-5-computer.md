---
title: "Depuraci&#243;n ASP.NET remota en un equipo remoto de IIS 7.5 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n ASP.NET remota en un equipo remoto de IIS 7.5
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar una aplicación web ASP.NET en un equipo de Windows Server 2008 R2 con IIS 7.5 y configurarla para la depuración remota. Las instrucciones siguientes explican cómo instalar y configurar una aplicación de Visual Studio 2015 MVC 4.5.2.  
  
## Crear la aplicación en el equipo de Visual Studio  
  
1.  Cree una nueva aplicación de MVC ASP.NET \(**Archivo \/ Nuevo \/ Proyecto**, a continuación, seleccione **Visual C\# \/ Web \/ Aplicación web ASP.NET** . En la sección de plantillas **ASP.NET 4.5.2**, seleccione **MVC**. Cancele la página **Configurar aplicación web de Microsoft Azure**. \) y asígnele el nombre **MyMVC**.  
  
2.  Abra el archivo HomeController.cs y establezca un punto de interrupción en el método `About()`.  
  
3.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Publicar**.  
  
4.  Para **Seleccionar un destino de publicación**, seleccione **Personalizado** y asigne al perfil el nombre **MyMVC**. Haga clic en **Siguiente**.  
  
5.  En la pestaña **Conexión**, configure el campo **Método de publicación** como **Sistema de archivos** y el campo **Ubicación de destino** con un directorio local. Haga clic en **Siguiente**.  
  
6.  Establezca la configuración en **Depurar**. Haga clic en **Publicar**.  
  
     Debe publicar la aplicación en el directorio local.  
  
## Implementar la aplicación en el equipo remoto de Windows Server  
 En esta sección se supone que el equipo de Windows Server 2008 R2 ya tiene IIS habilitado.  
  
1.  Instale ASP.NET:  
  
     **C:\\Windows\\Microsoft.NET\\Framework\(64\)\\v4.0.30319\\aspnet\_regiis.exe \-ir**  
  
2.  Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio a un directorio local \(que llamaremos **C:\\Publish**\) en el equipo de Windows Server.  
  
3.  Asegúrese de que el archivo web.config muestra la versión correcta de .NET Framework.  La versión de .NET Framework que se instala de forma predeterminada en este equipo es 4.0.30319, pero hemos creado una versión de ASP.NET 4.5.2. Si esta versión no está instalada en el equipo de Windows Server, debe cambiar la versión:  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  Abra el **Administrador de Internet Information Services \(IIS\)** y vaya a **Sitios**.  
  
5.  Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.  
  
6.  Establezca el campo **Alias** como **MyMVC** y el campo Grupo de aplicaciones como **ASP.NET v4.0**. Establezca la **Ruta de acceso física** como **C:\\Publish** \(donde haya copiado el directorio del proyecto ASP.NET\).  
  
7.  Para probar la implementación, haga clic con el botón secundario en **Sitio web predeterminado** y seleccione **Examinar**. Debería ver la página web.  
  
## Instalar al depurador remoto en el equipo de Windows Server  
 Para obtener instrucciones sobre cómo descargar el depurador remoto, vea [Depuración remota](../debugger/remote-debugging.md).  
  
 Para realizar la depuración remota de aplicaciones ASP.NET, puede iniciar el depurador remoto como servicio o ejecutar la aplicación del depurador remoto como administrador. Encontrará detalles sobre cómo ejecutar el depurador remoto como servicio en [Depuración remota](../debugger/remote-debugging.md).  
  
## Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio  
  
-   En el equipo de Visual Studio, abra la solución **MyMVC**.  
  
-   En Visual Studio, haga clic en **Depurar \/ Asociar al proceso**.  
  
-   Establezca el campo Calificador en **\<nombre del equipo remoto\>:4020**.  
  
-   Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles**.  
  
-   Active **Mostrar los procesos de todos los usuarios**.  
  
-   Busque **w3wp.exe** y haga clic en **Adjuntar**.  
  
-   Abra el sitio web del equipo remoto. En un explorador, vaya a **http:\/\/\<nombre del equipo remoto\>**.  
  
-   Debería ver la página web de ASP.NET. Haga clic en **Acerca de**.  
  
     Se alcanzará el punto de interrupción en Visual Studio.