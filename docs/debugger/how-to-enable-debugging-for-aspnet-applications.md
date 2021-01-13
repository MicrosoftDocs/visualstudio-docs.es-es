---
title: Habilitación de la depuración para aplicaciones de ASP.NET | Microsoft Docs
description: Obtenga información sobre cómo habilitar la depuración para aplicaciones de ASP.NET y ASP.NET Core en Visual Studio. Puede ejecutar el proceso en un servidor de IIS Express o en un servidor de IIS local.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
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
ms.openlocfilehash: 28f74c449e196d5eb0b3380d0ff1392db17e0b23
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903602"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Depuración de aplicaciones de ASP.NET o ASP.NET Core en Visual Studio

Puede depurar aplicaciones de ASP.NET o ASP.NET Core en Visual Studio. El proceso difiere entre ASP.NET y ASP.NET Core, y si se ejecuta en IIS Express o en un servidor de IIS local.

>[!NOTE]
>Los siguientes pasos y valores solo se aplican a la depuración de aplicaciones en un servidor local. La depuración de aplicaciones en un servidor IIS remoto usa **Asociar al proceso** y omite esta configuración. Para obtener más información e instrucciones para la depuración remota de aplicaciones de ASP.NET en IIS, vea [Depuración remota de ASP.NET en un equipo IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [Depuración remota de ASP.NET Core en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

El servidor de IIS Express integrado se incluye con Visual Studio. IIS Express es el servidor de depuración predeterminado para los proyectos de ASP.NET y ASP.NET Core, y está preconfigurado. Es la manera más fácil de depurar aplicaciones, y es ideal para realizar la depuración y las pruebas iniciales.

También puede depurar una aplicación de ASP.NET o ASP.NET Core en un servidor IIS local (versión 8.0 o posteriores) que esté configurado para ejecutar la aplicación. Para realizar la depuración en IIS local, debe cumplir los siguientes requisitos:

<a name="iis"></a>
- Si no está instalado, instale **ASP.NET y la carga de trabajo de desarrollo web**. Vuelva a ejecutar el Instalador de Visual Studio, seleccione **Modificar** y agregue esta carga de trabajo.

   ::: moniker range="vs-2017"
   En Visual Studio 2017, busque el componente **Compatibilidad con IIS en tiempo de desarrollo**. Asegúrese de que está seleccionado al agregar la carga de trabajo.
   ::: moniker-end
- Ejecute Visual Studio como administrador.
- Instale y configure correctamente IIS con las versiones adecuadas de ASP.NET o ASP.NET Core. Para obtener más información sobre el uso de IIS con ASP.NET Core, vea [Hospedaje de ASP.NET Core en Windows con IIS](/aspnet/core/host-and-deploy/iis/index). Para ASP.NET, consulte [Instalar IIS y los módulos de ASP.NET](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Asegúrese de que la aplicación se ejecuta en IIS sin errores.

## <a name="debug-aspnet-apps"></a>Depuración de aplicaciones de ASP.NET

IIS Express es el valor predeterminado y está preconfigurado. Si realiza la depuración en IIS local, asegúrese de que cumple los [requisitos para la depuración de IIS local](#iis).

1. Seleccione el proyecto de ASP.NET en el **Explorador de soluciones** de Visual Studio, haga clic en el icono **Propiedades** y presione **Alt**+**Entrar**, o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Web**.

1. En el panel **Propiedades**, en **Servidores**,
   - En IIS Express, seleccione **IIS Express** de la lista desplegable.
   - Para IIS local,
     1. Seleccione **IIS local** en la lista desplegable.
     1. Junto al campo **Dirección URL del proyecto**, seleccione **Crear directorio virtual**, si aún no ha configurado la aplicación en IIS.

1. En **Depuradores**, seleccione **ASP.NET**.

   ![Configuración del depurador de ASP.NET](media/dbg-aspnet-enable-debugging2.png "Configuración del depurador de ASP.NET")

1. Use **Archivo** > **Guardar elementos seleccionados** o presione **Ctrl**+**S** para guardar los cambios.

1. Para depurar la aplicación, en el proyecto, establezca puntos de interrupción en algunas secciones del código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración esté establecida en **Depurar** y el explorador que quiera aparezca en **IIS Express (\<Browser name>)** o **IIS local (\<Browser name>)** en el campo del emulador.

1. Para iniciar la depuración, seleccione **IIS Express (\<Browser name>)** o **IIS local (\<Browser name>)** en la barra de herramientas, seleccione **Iniciar depuración** en el menú **Depurar**, o bien presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, vea [Solución de problemas de depuración](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Depuración de aplicaciones ASP.NET Core

IIS Express es el valor predeterminado y está preconfigurado. Si realiza la depuración en IIS local, asegúrese de que cumple los [requisitos para la depuración de IIS local](#iis).

1. Seleccione el proyecto de ASP.NET Core en el **Explorador de soluciones** de Visual Studio, haga clic en el icono **Propiedades** y presione **Alt**+**Entrar**, o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Depurar**.

1. En el panel **Propiedades**, junto a **Perfil**,
   - En IIS Express, seleccione **IIS Express** de la lista desplegable.
   - En el caso de IIS local, seleccione el nombre de la aplicación en la lista desplegable o seleccione **Nuevo**, cree un nuevo nombre de perfil y seleccione **Aceptar**.

1. Junto a **Inicio**, seleccione **IIS Express** o **IIS** en la lista desplegable.

1. Asegúrese de que **Iniciar explorador** está seleccionado.

1. En **Variables de entorno**, asegúrese de que **ASPNETCORE_ENVIRONMENT** esté presente con un valor de **Desarrollo**. Si no es así, seleccione **Agregar** y agréguelo.

   ![Configuración del depurador de ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Configuración del depurador de ASP.NET Core")

1. Use **Archivo** > **Guardar elementos seleccionados** o presione **Ctrl**+**S** para guardar los cambios.

1. Para depurar la aplicación, en el proyecto, establezca puntos de interrupción en algunas secciones del código. En la barra de herramientas de Visual Studio, asegúrese de que la configuración esté establecida en **Depurar** y de que **IIS Express** o el nuevo nombre del perfil de IIS aparezcan en el campo emulador.

1. Para iniciar la depuración, seleccione **IIS Express** o **\<IIS profile name>** en la barra de herramientas, seleccione **Iniciar depuración** en el menú **Depurar**, o bien presione **F5**. El depurador se detiene en los puntos de interrupción. Si el depurador no puede alcanzar los puntos de interrupción, vea [Solución de problemas de depuración](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Solución de problemas de depuración

Si la depuración de IIS local no puede progresar hasta el punto de interrupción, siga estos pasos para solucionar el problema.

1. Inicie la aplicación web desde IIS y asegúrese de que se ejecuta correctamente. Deje la aplicación web en ejecución.

2. En Visual Studio, seleccione **Depurar > Asociar al proceso** o presione **Ctrl**+**Alt**+**P** y conéctese al proceso de ASP.NET o ASP.NET Core (normalmente, **w3wp.exe** o **dotnet.exe**). Para obtener más información, consulte [Asociar al proceso](attach-to-running-processes-with-the-visual-studio-debugger.md) y [Cómo: Buscar el nombre de un proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Si puede conectarse y alcanzar el punto de interrupción mediante **Asociar al proceso**, pero no mediante **Depurar** > **Iniciar depuración** o **F5**, es probable que un valor de configuración sea incorrecto en las propiedades del proyecto. Si usa un archivo HOSTS, asegúrese de que también está configurado correctamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configuración de la depuración en el archivo web.config

Los proyectos de ASP.NET tienen archivos *web.config* de forma predeterminada, que contienen la configuración de la aplicación y la información de inicio, incluida la configuración de depuración. Los archivos *web.config* deben estar configurados correctamente para la depuración. La configuración **Propiedades** de las secciones anteriores actualizan los archivos *web.config*, pero también puede configurarlos manualmente.

> [!NOTE]
> Los proyectos de ASP.NET Core no tienen inicialmente archivos *web.config*, pero usan *appsettings.json* y *archivos launchSettings.json* para la configuración de la aplicación y la información de inicio. La implementación de la aplicación crea un archivo *web.config* o archivos en el proyecto, pero normalmente no contiene información de depuración.

> [!TIP]
> El proceso de implementación puede actualizar la configuración de *web.config*, por lo que, antes de intentar realizar la depuración, asegúrese de que el archivo *web.config* esté configurado para la depuración.

**Para configurar manualmente un archivo *web.config* para la depuración:**

1. En Visual Studio, abra el archivo *web.config* del proyecto de ASP.NET.

2. *Web.config* es un archivo XML, por lo que contiene secciones anidadas marcadas por etiquetas. Localice la sección `configuration/system.web/compilation`. (Si el elemento `compilation` no existe, cree uno).

3. Asegúrese de que el atributo `debug` del elemento `compilation` se haya establecido en `true`. (Si el elemento `compilation` no contiene un atributo `debug`, agréguelo y establézcalo en `true`).

   Si usa IIS local en lugar del servidor de IIS Express predeterminado, asegúrese de que el valor del atributo `targetFramework` del elemento `compilation` coincida con el marco del servidor IIS.

   El elemento `compilation` del archivo *web.config* debe ser similar al del ejemplo siguiente:

   > [!NOTE]
   > Este ejemplo es un archivo *web.config* parcial. Normalmente hay secciones XML adicionales en los elementos `configuration` y `system.web`, y el elemento `compilation` también puede contener otros atributos y elementos.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automáticamente los cambios realizados en los archivos *web.config* y aplica la nueva configuración. No es preciso reiniciar el equipo ni el servidor IIS para que los cambios surtan efecto.

Un sitio web puede contener varios directorios y subdirectorios virtuales, con archivos *web.config* en cada uno de ellos. Las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] heredan los valores de los archivos *web.config* ubicados en niveles superiores de la ruta de acceso de la dirección URL. La configuración jerárquica del archivo *web.config* se aplica a todas las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] situadas debajo de ellas en la jerarquía. Al establecer una configuración diferente en un archivo *web.config* inferior en la jerarquía, se invalida la configuración del archivo superior.

Por ejemplo, si especifica `debug="true"` en <em>www.microsoft.com/aaa/web.config</em>, cualquier aplicación en la carpeta *aaa* o en cualquier subcarpeta de *aaa* hereda ese valor, excepto si una de esas aplicaciones reemplaza la configuración por su propio archivo *web.config*.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publicación en modo de depuración con el sistema de archivos

Hay varias maneras de publicar aplicaciones en IIS. En estos pasos se muestra cómo crear e implementar un perfil de publicación de depuración con el sistema de archivos. Para ello, debe ejecutar Visual Studio como administrador.

> [!IMPORTANT]
> Si cambia el código o lo recompila, debe repetir estos pasos para volver a publicarlo.

1. En Visual Studio, haga clic con el botón derecho en el proyecto y elija **Publicar**.

3. Elija **IIS, FTP, etc.** y haga clic en **Publicar**.

    ![Captura de pantalla del cuadro de diálogo "Elegir un destino de publicación" en Visual Studio. "IIS, FTP, Web Deploy" está seleccionado y el botón "Publicar" está resaltado.](media/dbg-aspnet-local-iis.png)

4. En el cuadro de diálogo **CustomProfile**, en **Método de publicación**, elija **Sistema de archivos**.

5. Para **Ubicación de destino**, seleccione **Examinar** ( **...** ).

   - En el caso de ASP.NET, seleccione **IIS local**, el sitio web que creó para la aplicación y, a continuación, **Abrir**.

     ![Publicación en ASP.NET en IIS](media/dbg-aspnet-local-iis1.png "Publicación de ASP.NET en IIS")

   - En el caso de ASP.NET Core, seleccione **Sistema de archivos**, la carpeta que configuró para la aplicación y, a continuación, **Abrir**.

1. Seleccione **Siguiente**.

1. En **Configuración**, seleccione **Depurar** en la lista desplegable.

1. Seleccione **Guardar**.

1. En el cuadro de diálogo **Publicar**, asegúrese de que aparece **CustomProfile** (o el nombre del perfil que acaba de crear) y de que **LastUsedBuildConfiguration** está establecido en **Depurar**.

1. Seleccione **Publicar**.

    ![Captura de pantalla del cuadro de diálogo Publicar, con la aplicación CustomProfile seleccionada, el botón Publicar resaltado y LastBuildConfiguration establecido en Depurar.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> El modo de depuración reduce en gran medida el rendimiento de la aplicación. Para obtener un mejor rendimiento, establezca `debug="false"` en el archivo *web.config* y especifique una compilación de versión al implementar una aplicación de producción o realizar mediciones de rendimiento.

## <a name="see-also"></a>Vea también
- [Depuración ASP.NET: requisitos del sistema](aspnet-debugging-system-requirements.md)
- [Cómo: Ejecución de un proceso de trabajo en una cuenta de usuario](how-to-run-the-worker-process-under-a-user-account.md)
- [Cómo: Búsqueda del nombre de un proceso de ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Depuración de aplicaciones web implementadas](debugging-deployed-web-applications.md)
- [Tutorial: Depuración de un formulario web](walkthrough-debugging-a-web-form.md)
- [Cómo: Depuración de excepciones de ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Depuración de aplicaciones web: errores y solución de problemas](debugging-web-applications-errors-and-troubleshooting.md)
