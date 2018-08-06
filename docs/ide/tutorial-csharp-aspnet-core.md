---
title: Introducción a C# y ASP.NET Core en Visual Studio
ms.custom: ''
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9df1cbae3b0233a8711ab6a287513d89670df4d4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177375"
---
# <a name="get-started-with-c-and-aspnet-in-visual-studio"></a>Introducción a C# y ASP.NET Core en Visual Studio

En este tutorial para el desarrollo de C# con ASP.NET Core mediante Visual Studio, creará una aplicación web de C# ASP.NET Core, le agregará código, explorará algunas características del IDE y ejecutará la aplicación.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="before-you-begin"></a>Antes de empezar

Esta es una sección rápida de P+F para presentar algunos conceptos clave.

### <a name="what-is-c"></a>¿Qué es C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) es un lenguaje de programación con seguridad de tipos y orientado a objetos que se ha diseñado para ser robusto y fácil de aprender.

### <a name="what-is-aspnet-core"></a>¿Qué es ASP.NET Core?

ASP.NET Core es un marco multiplataforma y de código abierto en el que se pueden crear aplicaciones conectadas a Internet, como por ejemplo, servicios y aplicaciones web. Las aplicaciones de ASP.NET Core se pueden ejecutar en .NET Core o .NET Framework. Puede desarrollar y ejecutar las aplicaciones multiplataforma ASP.NET Core en Windows, Mac y Linux. ASP.NET Core es código abierto en [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>¿Qué es Visual Studio?

Visual Studio es un conjunto de desarrollo integrado de herramientas de productividad para desarrolladores. Considérelo como un programa que se puede usar para crear programas y aplicaciones.

## <a name="start-developing"></a>Empezar a desarrollar

¿Listo para empezar a desarrollar? Vamos allá.

### <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de ASP.NET Core. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#**, expanda **Web** y después seleccione **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**, asigne el nombre *MyCoreApp* al archivo y, después, haga clic en **Aceptar**.

   ![Plantilla de proyecto Aplicación web ASP.NET Core en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Agregar una carga de trabajo (opcional)

Si no ve la plantilla de proyecto **Aplicación web ASP.NET Core**, puede obtenerla mediante la adición de la carga de trabajo **Desarrollo de ASP.NET y web**. Puede agregar esta carga de trabajo de una de las dos formas siguientes, según las actualizaciones de Visual Studio 2017 que estén instaladas en el equipo.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Usar el cuadro de diálogo Nuevo proyecto

1. Seleccione el vínculo **Abrir el Instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**.

   ![Seleccione el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después haga clic en **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Usar la barra del menú Herramientas

1. Cancele para salir del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, seleccione **Herramientas** > **Obtener herramientas y características...**.

2. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después haga clic en **Modificar**.

#### <a name="add-a-project-template"></a>Agregar una plantilla de proyecto

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione la plantilla de proyecto **Aplicación web (controlador de vista de modelos)**.

2. Seleccione **ASP.NET Core 2.0** en el menú desplegable superior. Si en la lista no aparece **ASP.NET Core 2.0**, debe instalarlo siguiendo el vínculo **Descargar** que aparece en una barra amarilla en la parte superior del cuadro de diálogo. Elija **Aceptar**.

   ![Cuadro de diálogo Nueva aplicación web ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Acerca de la solución

La solución sigue el patrón de arquitectura del controlador de vista de modelos (MVC) que separa una aplicación en tres componentes principales:

* En **Modelos** se incluyen clases que representan los datos de la aplicación. Las clases de modelo usan lógica de validación para aplicar las reglas de negocio para esos datos. Normalmente, los objetos de modelo recuperan y almacenan el estado del modelo en una base de datos.
* Las **Vistas** son los componentes que muestran la interfaz de usuario (IU) de la aplicación. Por lo general, esta interfaz de usuario muestra los datos del modelo.
* En los **Controladores** se incluyen las clases que controlan las solicitudes del explorador. Recuperan los datos del modelo y llaman a plantillas de vistas que devuelven una respuesta. En una aplicación MVC, la vista solo muestra información; el controlador controla y responde a la interacción y entrada del usuario.

El patrón de MVC ayuda a crear aplicaciones que son más fáciles de actualizar y probar que las tradicionales aplicaciones monolíticas.

### <a name="tour-your-solution"></a>Recorrido por la solución

 1. La plantilla de proyecto crea una solución con un solo proyecto de ASP.NET Core que se denomina **MyCoreApp**. Expanda el nodo del proyecto para exponer su contenido.

    ![Explorador de soluciones de ASP.NET en Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

 2. Abra el archivo *HomeController.cs* desde la carpeta **Controladores**.

     ![Archivo HomeController.cs en el Explorador de soluciones de Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 3. Ver el archivo *HomeController.cs*

     ![HomeController.cs en la ventana de código de Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 4. El proyecto también tiene una carpeta **Vistas** que contiene otras carpetas que se asignan a cada controlador (además de una para las vistas **compartidas**). Por ejemplo, el archivo CSHTML de la vista (una extensión de HTML) para la ruta de acceso */Home/About* estaría en *Views/Home/About.cshtml*. Abra ese archivo.

     ![Archivo About.cshtml en el Explorador de soluciones en Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

 5. En este archivo CSHTML se usa la sintaxis de Razor para representar HTML en función de una combinación de etiquetas estándar y C# en línea.

     ![About.cshtml en la ventana de código de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

   >[!NOTE]
   > Para más información al respecto, consulte la página [Introducción a C# y ASP.NET mediante la sintaxis Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 6. La solución también contiene una carpeta *wwwroot* que es la raíz del sitio web. Puede colocar el contenido estático del sitio (como CSS, imágenes y bibliotecas de JavaScript) directamente en las rutas de acceso en las que quiera que esté cuando se implemente el sitio.

     ![Carpeta wwwroot en el Explorador de soluciones en Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

 7. También hay una variedad de archivos de configuración que sirven para administrar el proyecto, sus paquetes y la aplicación en tiempo de ejecución. Por ejemplo, la [configuración](/aspnet/core/fundamentals/configuration) predeterminada de la aplicación se almacena en *appsettings.json*. Pero puede invalidar algunos o todos estos valores de forma individual en cada entorno, por ejemplo, proporcionando un archivo *appsettings.Development.json* para el entorno **Desarrollo**.

     ![Archivos de configuración en el Explorador de soluciones en Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Ejecutar y depurar la aplicación

1. Haga clic en el botón **IIS Express** del IDE para compilar y ejecutar la aplicación en modo de depuración. (O bien, presione **F5** o seleccione **Depurar > Iniciar depuración** desde la barra de menús).

   ![Haga clic en el botón IIS Express de Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Si recibe un mensaje de error que indica **No se puede conectar al servidor web "IIS Express"**, cierre Visual Studio y, luego, ábralo mediante la opción **Ejecutar como administrador** que aparece si hace clic con el botón derecho o en el menú contextual. A continuación, vuelva a ejecutar la aplicación.

2. Visual Studio inicia una ventana del explorador. Seleccione **Acerca de**.

   ![Seleccione Acerca de en la ventana del explorador de la aplicación](../ide/media/csharp-aspnet-browser-page.png)

 Entre otras cosas, la página **Acerca de** en el explorador representa el texto que se establece en el archivo *HomeController.cs*.

   ![Ver el texto de la página Acerca de](../ide/media/csharp-aspnet-browser-page-about.png)

3. Mantenga abierta la ventana del explorador y vuelva a Visual Studio. Abra *Controllers/HomeController.cs* si todavía no está abierto.

   ![Abrir el archivo HomeController.cs desde el Explorador de soluciones en Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

4. Establezca un punto de interrupción en la primera línea del método **About**. Para ello, haga clic en el margen o sitúe el cursor en la línea y presione **F9**.

  Esta línea establece algunos datos de la colección **ViewData** que se representan en la página CSHTML en *Views/Home/About.cshtml*.

   ![Establecer un punto de interrupción en la primera línea del método About de About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

5. Vuelva al explorador y actualice la página **Acerca de**. Esto activará el punto de interrupción en Visual Studio.

6. En Visual Studio, mueva el mouse sobre el miembro **ViewData** para ver sus datos.

   ![Ver el miembro ViewData del método About para ver más información](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

7. Quite el punto de interrupción de la aplicación con el mismo método usado para agregarlo.

8. Abra *Views/Home/About.cshtml*.

   ![Seleccionar About.cshtml en el Explorador de soluciones](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

9. Cambie el texto **"additional"** por **"changed"** y guarde el archivo.

   ![Cambie el texto que indica "additional" por texto que indique "changed"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

10. Vuelva a la ventana del explorador para ver el texto actualizado. (Actualice el explorador si no ve el texto que ha cambiado).

    ![Actualizar la ventana del explorador para ver el texto cambiado](../ide/media/csharp-aspnet-browser-page-about-changed.png)

11. Haga clic en el botón **Detener depuración** desde la barra de herramientas para detener la depuración. (O bien, presione **Mayús**+**F5**, o seleccione **Depurar** > **Detener depuración** desde la barra de menús).

   ![Haga clic en el botón Detener depuración de la barra de herramientas](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE de Visual Studio. Para que la aplicación se ejecute en un servidor público, haga clic en el botón siguiente.

> [!div class="nextstepaction"]
> [Implementar la aplicación en Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

También puede obtener información sobre cómo usar el marco Model-View-Controller (MVC) en ASP.NET Core siguiendo el tutorial [Introducción a ASP.NET Core MVC y Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x).
