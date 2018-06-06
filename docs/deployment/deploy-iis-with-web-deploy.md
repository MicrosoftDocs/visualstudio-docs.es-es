---
title: Implementar ASP.NET en IIS mediante Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794215"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Implementar ASP.NET en un equipo de IIS remoto mediante Web Deploy en Visual Studio

En este artículo se explica cómo instalar y configurar una aplicación de Visual Studio de 2017 ASP.NET MVC 4.5.2 e implementarla en IIS. Este artículo incluye pasos sobre cómo configurar una configuración básica de IIS en Windows server y la implementación de la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor ha requerido que se instalen y que esté listo para implementar. Si va a implementar una aplicación de ASP.NET Core, algunos pasos son diferentes. Para implementar una aplicación de ASP.NET Core, consulte [publicar una aplicación en IIS mediante la importación de la configuración de publicación](../deployment/tutorial-import-publish-settings-iis.md) para obtener instrucciones. En algunos escenarios ASP.NET y ASP.NET Core, resulta más rápido implementar en IIS mediante la importación de la configuración de publicación.

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 y IIS 8 (para Windows Server 2008 R2, los pasos del servidor son diferentes)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Crear ASP.NET 4.5.2 aplicación en el equipo de Visual Studio
  
1. En el equipo que ejecuta Visual Studio, elija **archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central elija **aplicación Web de ASP.NET (.NET Framework)** y, a continuación, haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificado, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Consulte los requisitos previos de este artículo para identificar las cargas de trabajo de Visual Studio necesarios, que se deben instalar.

1. Elija **MVC** (.NET Framework) y asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **generar > compilar solución** para compilar el proyecto.

## <a name="bkmk_configureIIS"></a> Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si está habilitada la configuración de seguridad mejorada de Internet Explorer (está habilitado de forma predeterminada), debe agregar algunos dominios como sitios de confianza para que le permitirán descargar algunos de los componentes de servidor web. Agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los dominios siguientes.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Al descargar el software, puede obtener las solicitudes para conceder permiso para cargar varias secuencias de comandos del sitio web y recursos. Algunos de estos recursos no son necesarias, pero para simplificar el proceso, haga clic en **agregar** cuando se le solicite.

## <a name="BKMK_deploy_asp_net"></a> Instalar ASP.NET 4.5 en Windows Server

Si desea información más detallada para instalar ASP.NET en IIS, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.

1. Utilice el instalador de plataforma Web (WPI) para instalar ASP.NET 4.5 (en el nodo del servidor en Windows Server 2012 R2, elija **obtener nuevos componentes de plataforma de Web** y, a continuación, busque ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si está utilizando Windows Server 2008 R2, instale ASP.NET 4 en lugar de utilizar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reiniciar el sistema (o ejecutar **net stop era /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

## <a name="BKMK_install_webdeploy"></a> Instale WebDeploy 3.6 en Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

1. Abra el Explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde va a implementar el proyecto ASP.NET más adelante.

2. Si no está ya abierto, abra el **Internet Information Services (IIS) Manager**. (En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio Web predeterminado**, elija **configuración básica**y establezca el **ruta de acceso física** a **C:\Publish**.

5. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

6. Establecer el **Alias** campo **MyASPApp**, acepte el valor predeterminado de grupo de aplicaciones (**DefaultAppPool**) y establezca el **ruta de acceso física** a  **C:\Publish**.

7. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo de grupo de aplicaciones en **ASP.NET v4.0** (ASP.NET 4.5 no es una opción para el grupo de aplicaciones).

8. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con permisos de lectura y ejecución. Si ninguno de estos usuarios están presente, agregue IUSR como un usuario con derechos de lectura y ejecución.

## <a name="bkmk_webdeploy"></a> Publique e implemente la aplicación mediante Web Deploy desde Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Además, puede que necesite leer la sección en [solución de problemas de puertos](#bkmk_openports).

## <a name="bkmk_openports"></a> Solución de problemas: Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, se abren los puertos necesarios por la instalación de ASP.NET y Web Deploy. Sin embargo, debe comprobar que los puertos estén abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir puertos a través de la [grupo de seguridad de red](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Puertos necesarios:

* 80 - necesarias para IIS
* 8172 - necesarios para que Web Deploy implementar la aplicación desde Visual Studio

1. Para abrir un puerto de servidor de Windows, abra la **iniciar** menú, busque **Firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**. Elija **siguiente** y en **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**, a continuación, **permitir la conexión**, haga clic en siguiente, y Agregue el nombre (**IIS**, **Web Deploy**, o **msvsmon**) para la regla de entrada.

    Si desea obtener más información acerca de cómo configurar Firewall de Windows, vea [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los otros puertos necesarios.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, había importado en Visual Studio e implementa una aplicación ASP.NET en IIS. También puede implementar mediante la importación de configuración de publicación.

> [!div class="nextstepaction"]
> [Implementar en IIS mediante la importación de la configuración de publicación](../deployment/tutorial-import-publish-settings-iis.md)