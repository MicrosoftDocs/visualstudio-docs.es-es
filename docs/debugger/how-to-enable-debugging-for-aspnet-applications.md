---
title: "Habilitar la depuración de aplicaciones ASP.NET | Documentos de Microsoft"
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e3c6dffbd99dbdd91753ce8d06ab139006692089
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Depurar aplicaciones de ASP.NET en Visual Studio

Puede depurar aplicaciones ASP.NET desde Visual Studio.

## <a name="requirements"></a>Requisitos

Para seguir las instrucciones de este tema, debe:

- IIS Express, que se incluye de forma predeterminada en Visual Studio 2012 y versiones posteriores

    O bien

- Una variable local IIS web server (versión 8.0 o posterior) que está configurado correctamente y se puede ejecutar la aplicación de ASP.NET sin errores.

Si el servidor es remoto, debe ejecutar el depurador remoto en el equipo remoto. Para depurar en un servidor IIS remoto, consulte [ASP.NET de depuración remota en un equipo con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Configurar opciones de depuración

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Habilitar la depuración ASP.NET en las propiedades del proyecto

1. Abra el proyecto ASP.NET en Visual Studio.

2. Haga clic en el proyecto en **el Explorador de soluciones**, elija **propiedades**y, a continuación, haga clic en el **Web** ficha.

    Para algunos tipos de proyecto, seleccione **Propiedades > depurar** en su lugar. En un proyecto de Web Forms ASP.NET, haga clic en el proyecto y seleccione **páginas de propiedades > Opciones de inicio**.
  
3.  En **Depuradores**, active la casilla **ASP.NET** .

    ![Configuración del depurador](../debugger/media/dbg-aspnet-enable-debugging.png "configuración del depurador")

> [!NOTE]
> Si crea un nuevo proyecto ASP.NET (**archivo > Nuevo proyecto**), la configuración de depuración ya está configurada correctamente.

### <a name="enable-debugging-in-the-webconfig-file"></a>Habilitar la depuración en el archivo web.config  

Para depurar una aplicación web, archivo web.config de la aplicación debe configurarse correctamente. Un archivo web.config es necesario si hospeda la aplicación en IIS o IIS Express.

Principales de ASP.NET, el archivo web.config se crea automáticamente cuando se implemente la aplicación (si todavía no está presente).

> [!TIP]
> El proceso de implementación puede actualizar la configuración de web.config. Por tanto, antes de intentar depurar, compruebe la configuración de web.config en el servidor.
  
1.  En Visual Studio, abra el archivo web.config del proyecto.  
  
    > [!NOTE]  
    > No se puede tener acceso al archivo web.config remotamente mediante un explorador Web. Por motivos de seguridad, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] configura Microsoft IIS para impedir el acceso directo del explorador a los archivos Web.config. Si se intenta tener acceso a un archivo de configuración mediante un explorador, obtendrá un error de acceso HTTP 403 (prohibido).  
  
2.  Busque el elemento `configuration/system.web/compilation` . Si el elemento compilation no existe, créelo.

    Web.config es un archivo XML, por lo que contiene secciones anidadas marcadas por etiquetas.
  
3.  Si el elemento `compilation` no tiene un atributo `debug` , agregue el atributo al elemento.  
  
4.  Asegúrese de que el valor del atributo `debug` está establecido en `true`.  
  
El archivo web.config debe ser similar al ejemplo siguiente:

> [!NOTE]
> En este ejemplo es un archivo web.config parcial. Secciones XML adicionales son normalmente presentes entre los elementos configuration y system.web. El elemento compilation puede contener también otros atributos y elementos.
  
#### <a name="example"></a>Ejemplo  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Si está utilizando un servidor externo en lugar del servidor de IIS Express de forma predeterminada, también debe asegurarse que la `targetFramework` valor de atributo coincide con la configuración en el servidor.

> [!IMPORTANT]
> Para obtener el mejor rendimiento, establezca una aplicación de producción en `debug=false` y especificar una versión de lanzamiento al compilar y publicar la aplicación.

## <a name="configure-project-settings-for-the-server"></a>Configurar el proyecto para el servidor

Para depurar en un servidor web local, establecer propiedades del proyecto. Para depurar en un servidor remoto, siga las instrucciones más completas se describe en [ASP.NET de depuración remota en IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) en su lugar.

1. En el **Web** ficha del proyecto de propiedades, seleccione **IIS Express** o **servidor externo** en el **Server** configuración. (Para algunos tipos de proyecto, estos valores aparecen en la **depurar** pestaña en su lugar.)

    ![Configuración del servidor](../debugger/media/dbg-aspnet-server-settings.png "configuración del servidor")

    IIS Express es el servidor predeterminado para ASP.NET y normalmente no requiere ninguna configuración especial. Se trata de la manera más fácil de depurar una aplicación ASP.NET.

    Para un proyecto Web Forms ASP.NET, haga clic en el proyecto, elija **páginas de propiedades > Opciones de inicio**y seleccione **usar servidor Web de manera predeterminada** o **usar servidor personalizado** () en lugar de **servidor externo**).

    ![Configuración del servidor para la aplicación de formularios Web Forms](../debugger/media/dbg-aspnet-server-settings-webforms.png "configuración de servidor para la aplicación de formularios Web Forms")

2. Si elige un servidor externo (personalizado), escriba la dirección URL correcta en el **dirección URL del proyecto** (o **URL Base**) campo.

    Si el servidor externo es IIS local, IIS debe estar instalado y configurado correctamente. Por ejemplo, la versión correcta de ASP.NET debe configurarse en IIS. Para obtener más información, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Si desea probar la implementación, así como la depuración, vea [implementación para probar](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Si el servidor externo es [remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), adjuntar al proceso en su lugar, y no se utiliza esta configuración de proyecto para la depuración.

## <a name="local-iis-web-server-configure-iis"></a>(Servidor web IIS local) Configurar IIS

Para IIS Express, no es necesario configurar el servidor web (omitir esta sección). IIS Express se recomienda para las pruebas iniciales.

Si está utilizando el servidor web IIS local, siga estos pasos.

1. Asegúrese de que IIS está instalado correctamente. Para obtener más información, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Asegúrese de que instale la versión correcta de ASP.NET en el servidor. Utilice el instalador de plataforma Web (WPI) para instalar ASP.NET 4.5 (en el nodo del servidor en Windows Server 2012 R2, elija **obtener nuevos componentes de plataforma de Web** y, a continuación, busque ASP.NET). Para instalar ASP.NET Core, consulte [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Si está utilizando Windows Server 2008 R2, instale ASP.NET 4 en lugar de utilizar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe - ir**

2. Abra la **de Internet Information Services (IIS) Manager**. (En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

5. Establecer el **Alias** campo **MyASPApp**, acepte el valor predeterminado de grupo de aplicaciones (**DefaultAppPool**) y establezca el **ruta de acceso física** a  **C:\inetpub\myNewFolder** (crear una nueva carpeta de la aplicación).

6. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo de grupo de aplicaciones en el valor correcto para la aplicación (use ASP.NET 4 para ASP.NET 4.5. Usar **código No administrado** principales de ASP.NET).

## <a name="local-iis-web-server-deploy-the-app"></a>(Servidor web IIS local) Implementar la aplicación

Para IIS Express, la aplicación web se implementa automáticamente al iniciar la depuración (omitir esta sección).

Si está utilizando el servidor web IIS local, siga estos pasos. Hay diferentes maneras de publicar la aplicación en IIS. En estos pasos, se muestra cómo crear y utilizar un perfil de publicación para que se pueden implementar mediante el sistema de archivos.

1. Reinicie Visual Studio como administrador.

    Para implementar con este método, necesita privilegios de administrador.

2. En Visual Studio, haga clic en el proyecto y elija **publicar** (para los formularios Web Forms, use **Publicar Web App**).

3. Elija **IIS, FTP, etc.** y haga clic en **publicar**.

    ![Publicar en IIS](../debugger/media/dbg-aspnet-local-iis.png "publicar en IIS")

    Para una aplicación de formularios Web Forms, elija **personalizado** en el cuadro de diálogo Publicar, escriba un nombre de perfil y elija **Aceptar**.

4. En el **método de publicación** , a continuación, elija **sistema de archivos**.

5. Para el **ubicación de destino**, haga clic en el **examinar** botón.

6. (ASP.NET Core) Elija **sistema de archivos** y seleccione la carpeta que creó anteriormente para la aplicación.

6. (ASP.NET) Elija **IIS Local**y seleccione el sitio web creado anteriormente y, a continuación, haga clic en **abiertos**.

    ![Publicar en IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "publicar en IIS")

    > [!TIP]
    > Si ve un mensaje que indica que el servidor web no está configurado correctamente, asegúrese de que está instalada la versión correcta de ASP.NET para IIS.

7. Haga clic en **siguiente** y elija un **depurar** configuración.

    > [!NOTE]
    > Si se implementa con una configuración de lanzamiento, se establece `debug=false` en el archivo web.config del servidor.

8. Haga clic en **guardar** para guardar la configuración de publicación y, a continuación, haga clic en **publicar**.

    > [!CAUTION]
    >  Si necesita realizar cambios en el código o volver a generar, debe volver a publicar y repita este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

## <a name="set-a-breakpoint-and-start-debugging"></a>Establecer un punto de interrupción e inicie la depuración

1. En el proyecto en Visual Studio, conjunto de un punto de interrupción en código que sepa que se ejecutará.

2. Para iniciar la depuración, presione **F5** (**Depurar > Iniciar depuración**).

3. Realizar acciones para ejecutar el código que contiene el punto de interrupción.

    El depurador realiza una pausa en la que estableció el punto de interrupción.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(IIS local) Solución de problemas: No se alcanza el punto de interrupción

1. Inicie la aplicación web de IIS y asegúrese de que se ejecuta correctamente. Deje la aplicación web que se ejecuta.

2. En Visual Studio, seleccione **Depurar > asociar al proceso** y conectar con el proceso ASP.NET (normalmente **w3wp.exe** o **dotnet.exe**). Para obtener más información, consulte [adjuntar al proceso](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Si es capaz de conectarse con **adjuntar al proceso** y puede alcanzar un punto de interrupción, pero no se puede iniciar la depuración con **F5**, es probable que una configuración es incorrecta en las propiedades del proyecto. Si está utilizando un archivo de HOSTS, compruebe que está configurado correctamente.

  
## <a name="robust-programming"></a>Programación sólida  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automáticamente los cambios realizados en los archivos Web.config y aplica la nueva configuración. No es preciso reiniciar el equipo ni el servidor IIS para que los cambios surtan efecto.  
  
Un sitio web puede contener varios directorios y subdirectorios virtuales, y pueden haber archivos Web.config en cada uno de ellos. Las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] heredan los valores de los archivos Web.config ubicados en niveles superiores de la ruta de acceso de la dirección URL. Los archivos de configuración jerárquicos permiten cambiar la configuración de varias aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] simultáneamente, por ejemplo de todas las aplicaciones que se encuentren por debajo en la jerarquía. Sin embargo, si `debug` se establece en un archivo inferior en la jerarquía, invalida el valor más alto.  
  
Por ejemplo, puede especificar `debug="true"` en www.microsoft.com/aaa/Web.config y cualquier aplicación en la carpeta aaa o en las subcarpetas de aaa hereda esa configuración. Por tanto, si su [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación está en www.microsoft.com/aaa/bbb, hereda ese valor, así como cualquier [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones en www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd y así sucesivamente. La única excepción es si una de esas aplicaciones reemplaza la configuración por medio de su propio archivo Web.config inferior.  
  
> [!IMPORTANT]
> Habilitar el modo de depuración en gran medida afecta al rendimiento de su [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación. No olvide deshabilitar el modo de depuración antes de implementar la aplicación o realizar controles de rendimiento.  
  
## <a name="see-also"></a>Vea también  
[Depuración ASP.NET: requisitos del sistema](aspnet-debugging-system-requirements.md)   
[Cómo: ejecutar el proceso de trabajo en una cuenta de usuario](how-to-run-the-worker-process-under-a-user-account.md)   
[Cómo: buscar el nombre del proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Depurar aplicaciones Web implementadas](debugging-deployed-web-applications.md)   
[Tutorial: Depurar un formulario Web Forms](walkthrough-debugging-a-web-form.md)   
[Cómo: depurar excepciones de ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Depuración de aplicaciones web: errores y solución de problemas](debugging-web-applications-errors-and-troubleshooting.md)
  