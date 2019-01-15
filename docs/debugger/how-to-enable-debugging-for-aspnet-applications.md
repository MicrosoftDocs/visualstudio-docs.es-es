---
title: Habilitar la depuración de aplicaciones ASP.NET | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c8723a97f5751b790c946055693064c3b7d12237
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881106"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Depurar aplicaciones ASP.NET o ASP.NET Core en Visual Studio

Puede depurar aplicaciones ASP.NET y ASP.NET Core en Visual Studio. El proceso varía entre ASP.NET y ASP.NET Core, y si se ejecuta en un servidor local de IIS o IIS Express. 

>[!NOTE]
>Los siguientes pasos y configuraciones se aplican solo a depurar aplicaciones en un servidor local. Depuración de aplicaciones en un servidor remoto de IIS server utiliza **asociar al proceso**e ignora esta configuración. Para obtener más información e instrucciones para aplicaciones ASP.NET de depuración remotas en IIS, consulte [depuración remota de ASP.NET en un equipo de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [depuración remota de ASP.NET Core en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

El servidor integrado de IIS Express se incluye con Visual Studio. IIS Express es el servidor de depuración predeterminado para los proyectos de ASP.NET y ASP.NET Core y está preconfigurado. Es la manera más fácil de depurar y ideal para una depuración y prueba inicial. 

También puede depurar una aplicación ASP.NET o ASP.NET Core en un servidor IIS local (versión 8.0 o posterior) que está configurada para ejecutar la aplicación. Para depurar en IIS local, debe cumplir los siguientes requisitos: 

<a name="iis"></a>
- Seleccione **IIS son compatibles con el tiempo de desarrollo** al instalar Visual Studio. (Si es necesario, vuelva a ejecutar el instalador de Visual Studio, seleccione **modificar**y agregue este componente.)
- Ejecutar Visual Studio como administrador. 
- Instalar y configurar correctamente IIS con las versiones de ASP.NET o ASP.NET Core adecuadas. Para obtener más información e instrucciones, consulte [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o [Host ASP.NET Core en Windows con IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Asegúrese de que la aplicación se ejecuta en IIS sin errores.

## <a name="debug-aspnet-apps"></a>Depuración de aplicaciones ASP.NET 

IIS Express es el valor predeterminado y está preconfigurado. Si está depurando en IIS Local, asegúrese de cumplir el [requisitos para la depuración local de IIS](#iis). 

1. Seleccione el proyecto ASP.NET en Visual Studio **el Explorador de soluciones** y haga clic en el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.
   
1. Seleccione el **Web** ficha.
   
1. En el **propiedades** panel, en **servidores**, 
   - Para IIS Express, seleccione **IIS Express** en la lista desplegable.
   - Para IIS local,
     1. Seleccione **IIS Local** en la lista desplegable.
     1. Junto a la **dirección URL del proyecto** campos, seleccione **crear directorio Virtual**, si aún no ha configurado la aplicación en IIS.
   
1. En **depuradores**, seleccione **ASP.NET**.
   
   ![Configuración del depurador ASP.NET](media/dbg-aspnet-enable-debugging2.png "configuración del depurador ASP.NET")
   
1. Use **archivo** > **guardar los elementos seleccionados** o **Ctrl**+**S** guardar los cambios. 
   
1. Para depurar la aplicación, en el proyecto, establecer puntos de interrupción en código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración está establecida en **depurar**, y aparece el explorador que desee en **IIS Express (\<nombre explorador >)** o **(deIISLocal\< Nombre del explorador >)** en el campo del emulador. 
   
1. Para iniciar la depuración, seleccione **IIS Express (\<nombre explorador >)** o **IIS Local (\<nombre explorador >)** en la barra de herramientas, seleccione **Iniciar depuración**desde el **depurar** menús o presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, consulte [solución de problemas de depuración](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Depurar aplicaciones de ASP.NET Core 

IIS Express es el valor predeterminado y está preconfigurado. Si está depurando en IIS Local, asegúrese de cumplir el [requisitos para la depuración local de IIS](#iis). 

1. Seleccione el proyecto de ASP.NET Core en Visual Studio **el Explorador de soluciones** y haga clic en el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.

1. Seleccione la pestaña **Depurar**.
   
1. En el **propiedades** panel, junto a **perfil**, 
   - Para IIS Express, seleccione **IIS Express** en la lista desplegable.
   - Para IIS local, seleccione el nombre de la aplicación en la lista desplegable o seleccione **New**, crear un nuevo nombre de perfil y seleccione **Aceptar**.
   
1. Junto a **iniciar**, seleccione **IIS Express** o **IIS** en la lista desplegable. 
   
1. Asegúrese de que **Iniciar explorador** está seleccionada.
   
1. En **variables de entorno**, asegúrese de que **ASPNETCORE_ENVIRONMENT** está presente con un valor de **desarrollo**. Si no, seleccione **agregar** y agréguelo.
   
   ![Configuración del depurador de ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "configuración del depurador de ASP.NET Core")
   
1. Use **archivo** > **guardar los elementos seleccionados** o **Ctrl**+**S** guardar los cambios. 
   
1. Para depurar la aplicación, en el proyecto, establecer puntos de interrupción en código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración está establecida en **depurar**y **IIS Express**, o el nuevo nombre de perfil IIS, aparece en el campo de emulador. 
   
1. Para iniciar la depuración, seleccione **IIS Express** o  **\<el nombre del perfil IIS >** en la barra de herramientas, seleccione **Iniciar depuración** desde el **depurar** menús o presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, consulte [solución de problemas de depuración](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Solución de problemas de depuración

Si la depuración de IIS local no avanza hasta el punto de interrupción, siga estos pasos para solucionar problemas. 

1. Inicie la aplicación web de IIS y asegúrese de que se ejecuta correctamente. Deje que se ejecute la aplicación web.
   
2. En Visual Studio, seleccione **Depurar > asociar al proceso** o presione **Ctrl**+**Alt**+**P**, y conectar al proceso de ASP.NET o ASP.NET Core (normalmente **w3wp.exe** o **dotnet.exe**). Para obtener más información, consulte [asociar al proceso](attach-to-running-processes-with-the-visual-studio-debugger.md) y [cómo buscar el nombre del proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Si puede conectarse y alcanzar el punto de interrupción mediante el uso de **asociar al proceso**, pero no mediante **depurar** > **Iniciar depuración** o **F5**, una configuración probablemente es incorrecta en las propiedades del proyecto. Si usa un archivo de HOSTS, asegúrese de que también está configurado correctamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurar la depuración en el archivo web.config  

Los proyectos de ASP.NET tienen *web.config* de forma predeterminada, los archivos que contienen tanto información de configuración e iniciar la aplicación, incluida la configuración de depuración. El *web.config* archivos deben estar configurados correctamente para la depuración. El **propiedades** configuración de actualización de las secciones anteriores la *web.config* archivos, pero puede también configurarlos manualmente. 

> [!NOTE]
> Proyectos de ASP.NET Core no tienen inicialmente *web.config* archivos, pero use *appsettings.json* y *launchSettings.json* archivos de configuración de la aplicación y lanzamiento información. Implementación de la aplicación crea un *web.config* archivo o archivos en el proyecto, pero normalmente no contienen información de depuración.

> [!TIP]
> El proceso de implementación se puede actualizar el *web.config* configuración, por lo que antes de intentar depurar, asegúrese de que el *web.config* está configurado para la depuración.
  
**Para configurar manualmente un *web.config* archivo para la depuración:**

1. En Visual Studio, abra el proyecto ASP.NET *web.config* archivo.  
  
2. *Web.config* es un archivo XML, por lo que contiene secciones anidadas marcadas por etiquetas. Busque el `configuration/system.web/compilation` sección. (Si el `compilation` elemento no existe, créela.)
  
3. Asegúrese de que el `debug` atributo en el `compilation` elemento está establecido en `true`. (Si la `compilation` elemento no contiene un `debug` atributo, agregarlo y establézcalo como `true`.) 
  
   Si está utilizando IIS local en lugar del servidor de IIS Express de forma predeterminada, asegúrese de que el `targetFramework` atributo valor en el `compilation` elemento coincide con el marco de trabajo en el servidor IIS.
  
   El `compilation` elemento de la *web.config* archivo debe ser similar al ejemplo siguiente:

   > [!NOTE]
   > En este ejemplo es una parcial *web.config* archivo. Hay secciones XML normalmente adicionales en el `configuration` y `system.web` elementos y el `compilation` elemento también puede contener otros elementos y atributos.
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automáticamente los cambios realizados en los archivos *web.config* y aplica la nueva configuración. No tiene que reiniciar el equipo o el servidor IIS para que los cambios surtan efecto.  
  
Un sitio Web puede contener varios directorios y subdirectorios virtuales, con *web.config* archivos en cada uno de ellos. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] las aplicaciones heredan los valores de configuración de *web.config* archivos en niveles superiores de la ruta de acceso de dirección URL. El jerárquica *web.config* configuración del archivo que se aplicará a todos los [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones por debajo de ellas en la jerarquía. Establecer una configuración diferente en un *web.config* inferior en la jerarquía del archivo invalida los valores en el archivo mayor.  
  
Por ejemplo, si especifica `debug="true"` en <em>www.microsoft.com/aaa/web.config</em>, cualquier aplicación en el *aaa* carpeta o en cualquier subcarpeta de *aaa* hereda ese valor, excepto si una de esas aplicaciones reemplaza la configuración con su propia *web.config* archivo.  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>Publicar en el modo de depuración con el sistema de archivos

Hay diferentes maneras de publicar aplicaciones en IIS. Estos pasos muestran cómo crear e implementar un perfil de publicación con el sistema de archivos de depuración. Para ello, debe ejecutar Visual Studio como administrador. 

> [!IMPORTANT]
> Si cambia el código o la regeneración, debe repetir estos pasos para volver a publicar. 

1. En Visual Studio, haga clic en el proyecto y elija **publicar**.

3. Elija **IIS, FTP, etcetera** y haga clic en **publicar**.

    ![Publicar en IIS](media/dbg-aspnet-local-iis.png "publicar en IIS")

4. En el **CustomProfile** cuadro de diálogo para **método Publish**, elija **sistema de archivos**.

5. Para **ubicación de destino**, seleccione **examinar** (**...** ).
   
   - Para ASP.NET, seleccione **IIS Local**, seleccione el sitio Web que creó para la aplicación y, a continuación, seleccione **abierto**.
     
     ![Publicar en ASP.NET a IIS](media/dbg-aspnet-local-iis1.png "publicar ASP.NET en IIS")
     
   - Para ASP.NET Core, seleccione **sistema de archivos**, seleccione la carpeta configurado para la aplicación y, a continuación, seleccione **abierto**.

1. Seleccione **Siguiente**. 

1. En **configuración**, seleccione **depurar** en la lista desplegable.

1. Seleccione **Guardar**.

1. En el **publicar** cuadro de diálogo, asegúrese de que **CustomProfile** (o el nombre del perfil que acaba de crear) aparezca, y **LastUsedBuildConfiguration** está establecido en  **Depurar**. 

1. Seleccione **Publicar**.

    ![Publicar en IIS](media/dbg-aspnet-local-iis-select-site.png "publicar en IIS")

> [!IMPORTANT]
> Modo de depuración reduce en gran medida el rendimiento de la aplicación. Para obtener el mejor rendimiento, establezca `debug="false"` en el *web.config* y especifique una compilación de versión al implementar una aplicación de producción o realizar mediciones de rendimiento.  

## <a name="see-also"></a>Vea también  
[Depuración ASP.NET: requisitos del sistema](aspnet-debugging-system-requirements.md)   
[Cómo: Ejecución de un proceso de trabajo en una cuenta de usuario](how-to-run-the-worker-process-under-a-user-account.md)   
[Cómo: Búsqueda del nombre de un proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Depuración de aplicaciones web implementadas](debugging-deployed-web-applications.md)   
[Tutorial: Depuración de un formulario web](walkthrough-debugging-a-web-form.md)   
[Cómo: Depuración de excepciones de ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Depuración de aplicaciones web: errores y solución de problemas](debugging-web-applications-errors-and-troubleshooting.md)
