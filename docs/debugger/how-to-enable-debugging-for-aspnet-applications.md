---
title: Habilitación de la depuración de aplicaciones de ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911349"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Depuración de aplicaciones de ASP.NET o ASP.NET Core en Visual Studio

Puede depurar aplicaciones de ASP.NET y ASP.NET Core en Visual Studio. El proceso difiere entre ASP.NET y ASP.NET Core, y si se ejecuta en IIS Express o en un servidor IIS local.

>[!NOTE]
>Los siguientes pasos y configuraciones solo se aplican a la depuración de aplicaciones en un servidor local. La depuración de aplicaciones en un servidor IIS remoto usa **asociar al proceso**y omite esta configuración. Para obtener más información e instrucciones para la depuración remota de aplicaciones ASP.NET en IIS, consulte [depuración remota de ASP.net en un equipo IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [ASP.net Core de depuración remota en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

El servidor de IIS Express integrado se incluye con Visual Studio. IIS Express es el servidor de depuración predeterminado para los proyectos de ASP.NET y ASP.NET Core y está preconfigurado. Es la manera más fácil de depurar y ideal para realizar pruebas y depuración iniciales.

También puede depurar una aplicación ASP.NET o ASP.NET Core en un servidor IIS local (versión 8,0 o superior) que esté configurado para ejecutar la aplicación. Para depurar en IIS local, debe cumplir los siguientes requisitos:

<a name="iis"></a>
- Seleccione **tiempo de desarrollo compatibilidad con IIS** al instalar Visual Studio. (Si es necesario, vuelva a ejecutar el Instalador de Visual Studio, seleccione **modificar**y agregue este componente).
- Ejecute Visual Studio como administrador.
- Instale y configure correctamente IIS con las versiones adecuadas de ASP.NET y/o ASP.NET Core. Para obtener más información e instrucciones, consulte [IIS 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o [ASP.net Core de host en Windows con IIS](/aspnet/core/host-and-deploy/iis/index).
- Asegúrese de que la aplicación se ejecuta en IIS sin errores.

## <a name="debug-aspnet-apps"></a>Depuración de aplicaciones ASP.NET

IIS Express es el valor predeterminado y está preconfigurado. Si realiza la depuración en IIS local, asegúrese de que cumple los [requisitos para la depuración de IIS local](#iis).

1. Seleccione el proyecto ASP.NET en Visual Studio **Explorador de soluciones** , haga clic en el icono **propiedades** , presione **Alt**+**entrar**o haga clic con el botón derecho y elija **propiedades**.

1. Seleccione la pestaña **Web** .

1. En el panel **propiedades** , en **servidores**,
   - En IIS Express, seleccione **IIS Express** en la lista desplegable.
   - Para IIS local,
     1. Seleccione **IIS local** en la lista desplegable.
     1. Junto al campo **dirección URL del proyecto** , seleccione **Crear directorio virtual**, si aún no ha configurado la aplicación en IIS.

1. En **depuradores**, seleccione **ASP.net**.

   ![Configuración del depurador de ASP.NET](media/dbg-aspnet-enable-debugging2.png "Configuración del depurador de ASP.NET")

1. Usar **archivo** > **guardar los elementos seleccionados** o **Ctrl**+**S** para guardar los cambios.

1. Para depurar la aplicación, en el proyecto, establezca puntos de interrupción en algún código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración esté establecida en **depurar**y de que el explorador que desee aparezca en **IIS Express (\<nombre del Explorador >)** o en el campo emulador **local de IIS (\<del > explorador)** .

1. Para iniciar la depuración, seleccione **IIS Express (nombre del explorador\<>)** o **el nombre de IIS local (\<Explorador >)** en la barra de herramientas, seleccione **iniciar depuración** en el menú **depurar** o presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, vea [solucionar problemas de depuración](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Depurar aplicaciones ASP.NET Core

IIS Express es el valor predeterminado y está preconfigurado. Si realiza la depuración en IIS local, asegúrese de que cumple los [requisitos para la depuración de IIS local](#iis).

1. Seleccione el proyecto de ASP.NET Core en Visual Studio **Explorador de soluciones** y haga clic en el icono **propiedades** , presione **Alt**+**entrar**o haga clic con el botón derecho y elija **propiedades**.

1. Seleccione la pestaña **Depurar**.

1. En el panel **propiedades** , junto a **perfil**,
   - En IIS Express, seleccione **IIS Express** en la lista desplegable.
   - En el caso de IIS local, seleccione el nombre de la aplicación en la lista desplegable o seleccione **nuevo**, crear un nuevo nombre de perfil y haga clic en **Aceptar**.

1. Junto a **iniciar**, seleccione **IIS Express** o **IIS** en la lista desplegable.

1. Asegúrese de que **iniciar el explorador** está seleccionado.

1. En **variables de entorno**, asegúrese de que **ASPNETCORE_ENVIRONMENT** esté presente con un valor de **desarrollo**. En caso contrario, seleccione **Agregar** y agréguelo.

   ![ASP.NET Core la configuración del depurador](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core la configuración del depurador")

1. Usar **archivo** > **guardar los elementos seleccionados** o **Ctrl**+**S** para guardar los cambios.

1. Para depurar la aplicación, en el proyecto, establezca puntos de interrupción en algún código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración esté establecida en **depurar**y de que **IIS Express**, o el nuevo nombre del perfil de IIS, aparezca en el campo emulador.

1. Para iniciar la depuración, seleccione **IIS Express** o **\<nombre del perfil de IIS >** en la barra de herramientas, seleccione **iniciar depuración** en el menú **depurar** o presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, vea [solucionar problemas de depuración](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Solucionar problemas de depuración

Si la depuración de IIS local no puede progresar al punto de interrupción, siga estos pasos para solucionar el problema.

1. Inicie la aplicación web desde IIS y asegúrese de que se ejecuta correctamente. Deje la aplicación web en ejecución.

2. En Visual Studio, seleccione **Depurar > adjuntar al proceso** o presione **Ctrl**+**Alt**+**P**y conéctese al proceso de ASP.net o ASP.net Core (normalmente **w3wp. exe** o **dotnet. exe**). Para obtener más información, vea [asociar al proceso](attach-to-running-processes-with-the-visual-studio-debugger.md) y [Cómo buscar el nombre del proceso ASP.net](how-to-find-the-name-of-the-aspnet-process.md).

Si puede conectarse y alcanzar el punto de interrupción utilizando **asociar al proceso**, pero no mediante **depurar** > **iniciar depuración** o **F5**, es probable que un valor de configuración sea incorrecto en las propiedades del proyecto. Si usa un archivo de hosts, asegúrese de que también esté configurado correctamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurar la depuración en el archivo Web. config

Los proyectos de ASP.NET tienen archivos *Web. config* de forma predeterminada, que contienen la configuración de la aplicación y la información de inicio, incluida la configuración de depuración. Los archivos *Web. config* deben estar configurados correctamente para la depuración. La configuración de **las propiedades** de las secciones anteriores actualiza los archivos *Web. config* , pero también puede configurarlos manualmente.

> [!NOTE]
> ASP.NET Core proyectos no tienen inicialmente archivos *Web. config* , pero usan los archivos *appSettings. JSON* y *launchSettings. JSON* para la configuración de la aplicación y la información de inicio. La implementación de la aplicación crea un archivo *Web. config* o archivos en el proyecto, pero no contienen normalmente información de depuración.

> [!TIP]
> El proceso de implementación puede actualizar la configuración de *Web. config* , por lo que antes de intentar depurar, asegúrese de que el *archivo Web. config* está configurado para la depuración.

**Para configurar manualmente un archivo *Web. config* para la depuración:**

1. En Visual Studio, abra el archivo *Web. config* del proyecto ASP.net.

2. *Web. config* es un archivo XML, por lo que contiene secciones anidadas marcadas con etiquetas. Localice la sección `configuration/system.web/compilation`. (Si el elemento de `compilation` no existe, créelo).

3. Asegúrese de que el atributo `debug` del elemento `compilation` está establecido en `true`. (Si el elemento `compilation` no contiene un atributo `debug`, agréguelo y establézcalo en `true`).

   Si usa IIS local en lugar del servidor de IIS Express predeterminado, asegúrese de que el valor del atributo `targetFramework` del elemento `compilation` coincide con el marco del servidor IIS.

   El elemento `compilation` del archivo *Web. config* debe ser similar al del ejemplo siguiente:

   > [!NOTE]
   > Este ejemplo es un archivo *Web. config* parcial. Normalmente hay secciones XML adicionales en los elementos `configuration` y `system.web`, y el elemento `compilation` también puede contener otros atributos y elementos.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automáticamente los cambios realizados en los archivos *web.config* y aplica la nueva configuración. No es necesario reiniciar el equipo o el servidor IIS para que los cambios surtan efecto.

Un sitio web puede contener varios directorios virtuales y subdirectorios, con archivos *Web. config* en cada uno de ellos. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones heredan los valores de configuración de los archivos *Web. config* en los niveles superiores de la ruta de dirección URL. La configuración del archivo *Web. config* jerárquico se aplica a todas las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debajo de ellas en la jerarquía. Al establecer una configuración diferente en un archivo *Web. config* situado en una posición inferior de la jerarquía, se invalida la configuración del archivo superior.

Por ejemplo, si especifica `debug="true"` en <em>www.Microsoft.com/AAA/Web.config</em>, las aplicaciones de la carpeta *AAA* o de cualquier subcarpeta de *AAA* heredarán esa configuración, excepto si una de esas aplicaciones invalida la configuración con su propio *archivo Web. config.* filesystem.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publicar en modo de depuración con el sistema de archivos

Hay diferentes maneras de publicar aplicaciones en IIS. En estos pasos se muestra cómo crear e implementar un perfil de publicación de depuración con el sistema de archivos. Para ello, debe ejecutar Visual Studio como administrador.

> [!IMPORTANT]
> Si cambia el código o vuelve a generarlo, debe repetir estos pasos para volver a publicarlo.

1. En Visual Studio, haga clic con el botón derecho en el proyecto y elija **publicar**.

3. Elija **IIS, FTP, etc.** y haga clic en **publicar**.

    ![Publicar en IIS](media/dbg-aspnet-local-iis.png "Publicación en IIS")

4. En el cuadro de diálogo **CustomProfile** , en **método de publicación**, seleccione **sistema de archivos**.

5. En **Ubicación de destino**, seleccione **examinar** ( **...** ).

   - En ASP.NET, seleccione **IIS local**, seleccione el sitio web que creó para la aplicación y, a continuación, seleccione **abrir**.

     ![Publicar en ASP.NET en IIS](media/dbg-aspnet-local-iis1.png "Publicar ASP.NET en IIS")

   - En ASP.NET Core, seleccione **sistema de archivos**, seleccione la carpeta que configuró para la aplicación y, a continuación, seleccione **abrir**.

1. Seleccione **Siguiente**.

1. En **configuración**, seleccione **depurar** en la lista desplegable.

1. Seleccione **Guardar**.

1. En el cuadro de diálogo **publicar** , asegúrese de que **CustomProfile** (o el nombre del perfil que acaba de crear) aparece y **LastUsedBuildConfiguration** está establecido en **debug (depurar**).

1. Seleccione **Publicar**.

    ![Publicar en IIS](media/dbg-aspnet-local-iis-select-site.png "Publicación en IIS")

> [!IMPORTANT]
> El modo de depuración reduce en gran medida el rendimiento de la aplicación. Para obtener el mejor rendimiento, establezca `debug="false"` en el *archivo Web. config* y especifique una compilación de versión al implementar una aplicación de producción o realizar mediciones de rendimiento.

## <a name="see-also"></a>Vea también
- [Depuración ASP.NET: requisitos del sistema](aspnet-debugging-system-requirements.md)
- [Ejecución del proceso de trabajo en una cuenta de usuario](how-to-run-the-worker-process-under-a-user-account.md)
- [Búsqueda del nombre de un proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Depuración de aplicaciones web implementadas](debugging-deployed-web-applications.md)
- [Tutorial: Depurar un formulario web](walkthrough-debugging-a-web-form.md)
- [Depuración de excepciones de ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Depurar aplicaciones web: errores y solución de problemas](debugging-web-applications-errors-and-troubleshooting.md)
