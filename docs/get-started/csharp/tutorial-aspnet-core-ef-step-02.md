---
title: 'Paso 2: Creación de la primera aplicación web de ASP.NET Core'
description: Cree su primera aplicación web de ASP.NET Core con este tutorial en vídeo y con instrucciones detalladas.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 21959c4a0cc2b961eca43ab9724369c7aea8444b
ms.sourcegitcommit: ab18c9d850192fc9ccec10961f1126e8b0cba8da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73061133"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Paso 2: Creación de la primera aplicación web de ASP.NET Core

Cree su primera aplicación web de ASP.NET Core con este tutorial en vídeo y con instrucciones detalladas.

_Vea este vídeo y siga el tutorial para crear su primera aplicación de ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Inicio de Visual Studio 2019 y creación de un proyecto

Inicie Visual Studio 2019 y haga clic en **Crear proyecto**. Elija **Aplicación web de ASP.NET Core**. Elija la plantilla **Aplicación web** y mantenga el nombre y la ubicación de proyecto predeterminados. En la lista desplegable de versiones de ASP.NET Core, elija **ASP.NET Core 2.1** o **ASP.NET Core 2.2**. Haga clic en **Crear**. Para obtener instrucciones detalladas, vea [el vídeo anterior de esta serie de tutoriales](tutorial-aspnet-core-ef-step-01.md).

![Elección de opciones de proyecto de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Asegúrese de elegir ASP.NET Core 2.1 o ASP.NET Core 2.2. Este tutorial no es compatible con ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Exploración del nuevo proyecto

A la derecha de la ventana del explorador de soluciones, puede ver el contenido del nuevo proyecto. Se describe aquí.

![Proyecto de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

La carpeta *wwwroot* contiene archivos estáticos que serán accesibles públicamente desde la aplicación web. Normalmente, contiene hojas de estilo, archivos de script del lado cliente e imágenes.

### <a name="pages"></a>Páginas

La carpeta *Pages* contiene las páginas de Razor Pages del sitio. La plantilla predeterminada proporciona varias páginas, incluida *Index.cshtml*, que es la página principal de la aplicación, así como About, Contact, etc.

### <a name="appsettingsjson"></a>appsettings.json

Este archivo contiene los valores de configuración del sitio, en formato JSON.

### <a name="programcs"></a>Program.cs

Este archivo actúa como punto de entrada de la aplicación. Cuando se ejecuta la aplicación, su método Main es el primer método que se ejecuta y es responsable de crear el host de web que contendrá la aplicación.

### <a name="startupcs"></a>Startup.cs

El host de web creado en *Program.cs* hace referencia a la clase Startup y llama a sus métodos para configurar la aplicación. El método ConfigureServices es responsable de configurar los servicios que va a usar la aplicación. El método `Configure` configura de la canalización de solicitudes HTTP de la aplicación. Cada solicitud se pasa por esta canalización e interactúa con cada parte de *middleware* a medida que lo hace.

### <a name="indexcshtml"></a>Index.cshtml

La página principal del sitio incluye algún marcado HTML y código de Razor del lado servidor. Utiliza Razor para especificar el modelo de página, `IndexModel`, que se encuentra en el archivo *Index.cshtml.cs* asociado. También define el título de página estableciendo un valor de ViewData. Este valor se lee del archivo *\_Layout.cshtml*, que se encuentra en la carpeta Shared dentro de la carpeta Pages. El archivo de diseño es compartido por varias páginas de Razor Pages y proporciona la apariencia común de la aplicación. El contenido de cada página se representa en el HTML del archivo de diseño.

## <a name="run-the-application"></a>Ejecutar la aplicación

Ejecute ahora la aplicación y véala en el explorador. Puede ejecutar la aplicación mediante **Ctrl**+**F5** o eligiendo **Depurar** > **Iniciar sin depurar** en el menú de Visual Studio.

## <a name="customize-the-application"></a>Personalización de la aplicación

Agregue una propiedad al archivo *Index.cshtml.cs* y, en el controlador `OnGet`, establezca su valor en la hora actual:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Reemplace el contenido de `<div>` en *Index.cshtml* por este marcado:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Vuelva a ejecutar la aplicación. Debería ver que ahora la página muestra la hora actual, pero siempre es medianoche. Eso no es correcto.

![Proyecto de ASP.NET Core en Visual Studio 2019 en el explorador](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Depurar la aplicación

Agregue un punto de interrupción al método `OnGet` donde asignamos un valor a `Time` que es la hora de inicio de la depuración de la aplicación.

La ejecución se detiene en la línea y puede verse que `DateTime.Today` incluye la fecha pero la hora es siempre medianoche porque no incluye datos de hora. 

![Proyecto de ASP.NET Core en Visual Studio 2019 en el explorador](media/vs-2019/vs2019-breakpoint.png)

Cámbielo para que se use `DateTime.Now` y continúe la ejecución. El nuevo código para `OnGet` debe ser:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Ahora debería ver la hora real del servidor en el explorador cuando navegue a la aplicación.

> [!NOTE]
> Los resultados pueden diferir de la imagen, ya que el formato de salida de ToShortDateTimeString depende de la configuración de la referencia cultural actual. Vea <xref:System.DateTime.ToShortTimeString>.

![Proyecto de ASP.NET Core en Visual Studio 2019 en el explorador](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Pasos siguientes

En el vídeo siguiente, aprenderá a agregar compatibilidad con datos a la aplicación.

[Tutorial: Trabajo con datos en la aplicación de ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Vea también

- [Tutorial: Creación de una aplicación web de páginas de Razor con ASP.NETCore](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
