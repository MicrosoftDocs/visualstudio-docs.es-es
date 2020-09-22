---
title: Depuración remota ASP.NET en un equipo remoto de IIS 7,5 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842802"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Depuración remota de ASP.NET en un equipo remoto de IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar una aplicación Web de ASP.NET en un equipo con Windows Server con IIS y configurarla para la depuración remota. En esta guía se explica cómo instalar y configurar una aplicación de Visual Studio 2015 MVC 4.5.2, implementarla en IIS y asociar el depurador remoto desde Visual Studio.

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 10
* Windows Server 2008 R2 e IIS 7,5

La mayor parte de la información de este artículo también se aplica a la depuración remota de una aplicación ASP.NET Core, salvo que la implementación de aplicaciones de ASP.NET Core es diferente y requiere pasos adicionales. Para implementar una aplicación ASP.NET Core en IIS, deberá completar todas las secciones de [este artículo](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Requisitos previos: instalar el depurador remoto en el equipo con Windows Server

Para obtener instrucciones sobre cómo descargar el depurador remoto en el equipo con Windows Server, vea [depuración remota](../debugger/remote-debugging.md).

Para realizar la depuración remota de aplicaciones de ASP.NET, puede ejecutar la aplicación del Depurador remoto como administrador o iniciar el depurador remoto como un servicio. Encontrará detalles sobre cómo ejecutar el depurador remoto como servicio en [Remote Debugging](../debugger/remote-debugging.md).

Una vez instalado, asegúrese de que el depurador remoto se está ejecutando en el equipo de destino. (Si no es así, busque el **Depurador remoto** en el menú **Inicio** . ) La ventana del Depurador remoto tiene el siguiente aspecto. (4020 es el número de puerto predeterminado)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Crear la aplicación en el equipo de Visual Studio  
  
1. Cree una nueva aplicación de MVC ASP.NET (**Archivo / Nuevo / Proyecto**, a continuación, seleccione **Visual C# / Web / Aplicación web ASP.NET** . En la sección de plantillas **ASP.NET 4.5.2** , seleccione **MVC**. Asegúrese de que **host en la nube** no está seleccionado en la sección Azure. Asigne al proyecto el nombre **MyMVC**.)
1. Abra el archivo HomeController.cs y establezca un punto de interrupción en el método `About()` .
1. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Publicar**.
1. Para **Seleccionar un destino de publicación**, seleccione **Personalizado** y asigne al perfil el nombre **MyMVC**. Haga clic en **Siguiente**.
1. En la pestaña **Conexión** , configure el campo **Método de publicación** como **Sistema de archivos** y el campo **Ubicación de destino** con un directorio local. Haga clic en **Siguiente**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Establezca la configuración en **Depurar**. Haga clic en **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Debe publicar la aplicación en el directorio local.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Implementar la aplicación ASP.NET en el equipo remoto de Windows Server

 En esta sección se supone que el equipo con Windows Server ya tiene IIS habilitado. En Windows Server 2012 R2, consulte [configuración de IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) para habilitar IIS. (Puede omitir otras secciones de este artículo a menos que esté intentando implementar una aplicación ASP.NET Core. Por ASP.NET Core, siga los pasos del artículo para implementar la aplicación en lugar de los pasos que se describen aquí.
1. Instale ASP.NET use los componentes de la plataforma web para instalar ASP.NET 4,5 (desde el nodo de servidor en Windows Server 2012 R2, elija **obtener nuevos componentes de plataforma web** y busque ASP.net).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    En Windows Server 2008 R2, instale ASP.NET 4 en su lugar con este comando:   **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-ir**
1. Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio a un directorio local (que llamaremos **C:\Publish**) en el equipo de Windows Server. Puede copiar el proyecto manualmente, usar xcopy, Web Deploy, Robocopy, PowerShell u otras opciones.

    > [!CAUTION]
    > Si necesita realizar cambios en el código o recompilar, debe volver a publicar y repetir este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.
1. Asegúrese de que el archivo web.config muestra la versión correcta de .NET Framework.  Por ejemplo, la versión de .NET Framework instalada de forma predeterminada en Windows Server 2008 R2 es 4.0.30319, pero se ha creado una versión de ASP.NET 4.5.2. Si se está ejecutando una aplicación de ASP.NET 4,0 en el equipo con Windows Server, debe cambiar la versión:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.
1. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.
1. Establezca el campo **alias** en **MyMVC** y el campo grupo de aplicaciones en **ASP.NET v 4.0** (ASP.net 4,5 no es una opción para el grupo de aplicaciones). Establezca la **Ruta de acceso física** como **C:\Publish** (donde haya copiado el directorio del proyecto ASP.NET).

    >[!NOTE] 
    > En el caso de las aplicaciones ASP.NET Core, establezca el campo Grupo de aplicaciones en **sin código administrado**.
1. Pruebe la implementación; para ello, haga clic con el botón secundario en **sitio web predeterminado** y seleccione **examinar**.
    Si ha implementado correctamente la aplicación, verá la Página Web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución **MyMVC** .
1. En Visual Studio, haga clic en **depurar/asociar al proceso** (**Ctrl + Alt + P**).
1. Establezca el campo calificador en ** \<remote computer name> : 4020**.
1. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve ningún proceso, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es obligatorio). Use `ipconfig` en una línea de comandos para obtener la dirección IPv4.
1. Active  **Mostrar los procesos de todos los usuarios**.
1. Busque **w3wp.exe** y haga clic en **Adjuntar**.

     Para encontrar rápidamente el nombre del proceso, escriba la primera letra del proceso.
     
    >[!NOTE]
    > En el caso de una aplicación ASP.NET Core, elija el proceso de dnx.exe en lugar de w3wp.exe. (Este nombre de proceso puede cambiar en una próxima versión).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<remote computer name>** .
    
    Debería ver la página web de ASP.NET.
1. En la Página Web de ASP.NET, haga clic en el vínculo a la página **About** .

    Se alcanzará el punto de interrupción en Visual Studio.
