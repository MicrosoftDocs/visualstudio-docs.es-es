---
title: Introducción a ASP.NET Core
description: En este artículo se describe cómo empezar a trabajar con ASP.NET en Visual Studio para Mac, incluida la instalación y la creación de un nuevo proyecto.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: 257d60d87a743d5c5e1099ee443c7bdb38055cca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985600"
---
# <a name="getting-started-with-aspnet-core"></a>Introducción a ASP.NET Core

 Visual Studio para Mac facilita el desarrollo del servicio de su aplicación gracias a su compatibilidad con la plataforma de desarrollo web de ASP.NET Core más reciente. ASP.NET Core se ejecuta en .NET Core, la evolución más reciente de .NET Framework y el tiempo de ejecución. Se ha ajustado para ofrecer un rendimiento rápido, se ha factorizado para admitir tamaños de instalación pequeños y se ha reinventado para ejecutarse en Linux y macOS, además de Windows.

## <a name="installing-net-core"></a>Instalación de .NET Core

.NET Core 2.1 se instala automáticamente cuando se instala Visual Studio para Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Crear una aplicación de ASP.NET Core en Visual Studio para Mac

Abra Visual Studio para Mac. En la pantalla de inicio, seleccione **Nuevo proyecto...**.

![Cuadro de diálogo Nuevo proyecto](media/asp-net-core-2019-new-asp-core.png)

Se mostrará el cuadro de diálogo Nuevo proyecto, que le permite seleccionar una plantilla para crear la aplicación.

Hay una serie de proyectos que le proporcionarán una plantilla predefinida para empezar a compilar la aplicación de ASP.NET Core. Estos son:

- **.NET Core > Vacío**
- **.NET Core > API**
- **.NET Core > Aplicación web**
- **.NET Core > Aplicación web (Modelo-Vista-Controlador)**

![Opciones de proyecto de ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Seleccione **ASP.NET Core Empty Web Application** (Aplicación web vacía de ASP.NET Core) y pulse **Siguiente**. Asígnele un nombre al proyecto y pulse **Crear**. Esto crea una aplicación de ASP.NET Core, que debería parecerse a la imagen siguiente:

![Vista de nuevo proyecto vacío de ASP.NET Core](media/asp-net-core-2019-empty-project.png)

La aplicación web vacía de ASP.NET Core crea una aplicación web con dos archivos predeterminados: **Program.cs** y **Startup.cs**, que se explican a continuación. También crea una carpeta Dependencias, que contiene las dependencias de paquetes NuGet del proyecto, como ASP.NET Core, .NET Core Framework y los destinos de MSBuild que compilan el proyecto:

![Panel de solución con las dependencias](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Abra e inspeccione el archivo **Program.cs** del proyecto. Observe que suceden varias cosas en el método `Main`, la entrada en la aplicación:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Una aplicación de ASP.NET Core crea un servidor web en su método principal, para lo que configura e inicia un host mediante una instancia de [`WebHostBuilder`](/aspnet/core/fundamentals/hosting). Este generador proporciona métodos que permiten configurar el host. En la aplicación de plantilla se usan las configuraciones siguientes:

* `.UseStartup<Startup>()`: especifica la clase Startup.

Aunque también se pueden agregar configuraciones adicionales, tales como:

* `UseKestrel`: especifica que la aplicación usará el servidor Kestrel.
* `UseContentRoot(Directory.GetCurrentDirectory())`: usa la carpeta raíz del proyecto web como raíz del contenido de la aplicación cuando la aplicación se inicia desde esta carpeta.
* `.UseIISIntegration()`: especifica que la aplicación debería funcionar con IIS. Para usar IIS con ASP.NET Core, deben especificarse `UseKestrel` y `UseIISIntegration`.

### <a name="startupcs"></a>Startup.cs

La clase Startup de la aplicación se especifica en el método `UseStartup()` en `CreateWebHostBuilder`. Es en esta clase donde especificará la canalización de control de solicitudes y donde configurará los servicios.

Abra e inspeccione el archivo **Startup.cs** del proyecto:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }
    }
```

La clase Startup siempre debe cumplir las reglas siguientes:

- Siempre debe ser pública.
- Debe contener los dos métodos públicos `ConfigureServices` y `Configure`.

El método `ConfigureServices` define los servicios que usará la aplicación.

`Configure` permite crear la canalización de solicitudes mediante [software intermedio](/aspnet/core/fundamentals/middleware). Se trata de componentes que se usan dentro de una canalización de aplicación de ASP.NET para controlar las solicitudes y las respuestas. La canalización HTTP está formada por una serie de delegados de solicitud, a los que se llama en secuencia. Cada delegado puede elegir controlar la solicitud o pasarla al delegado siguiente.

Puede configurar los delegados mediante los métodos `Run`, `Map` y `Use` en `IApplicationBuilder`, pero el método `Run` nunca llamará al delegado siguiente y siempre se debe usar al final de la canalización.

El método `Configure` de la plantilla predefinida está diseñado para realizar una serie de acciones. En primer lugar, configura una página de control de excepciones para su uso durante el desarrollo. Después, envía una respuesta a la página web que realiza la solicitud con un simple "Hello World".

Este sencillo proyecto Hello, World se puede ejecutar ahora sin necesidad de agregar más código. Para ejecutar la aplicación y verla en el explorador, pulse el botón Reproducir (el botón triangular) en la barra de herramientas:

![Ejecutar la aplicación](media/asp-net-core-2019-run-debug.png)

Visual Studio para Mac usa un puerto aleatorio para iniciar el proyecto web. Para averiguar qué puerto es, abra la salida de la aplicación, que aparece en **Vista > Paneles**. La salida debería parecerse a la que se muestra a continuación:

![Salida de la aplicación en la que se muestra el puerto de escucha](media/asp-net-core-image6.png)

Cuando el proyecto se está ejecutando, el explorador web predeterminado debe iniciarse y conectar con la dirección URL indicada en la salida de la aplicación. También puede abrir el explorador que prefiera y escribir `http://localhost:5000/`, lo que reemplaza `5000` por el puerto que Visual Studio genera en la salida de la aplicación. Debería ver el texto `Hello World!`:

![explorador en el que se muestra el texto](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Agregar un controlador

Las aplicaciones de ASP.NET Core usan el modelo de diseño Controlador de vista de modelos (MVC) para proporcionar una separación lógica de las responsabilidades para cada elemento de la aplicación. MVC consta de los siguientes elementos:

- **Model**: clase que representa los datos de la aplicación.
- **Vista**: muestra la interfaz de usuario de la aplicación (que suelen ser los datos del modelo).
- **Controller**: clase que controla las solicitudes del explorador y responde a la entrada y la interacción del usuario.

Para obtener más información sobre el uso de MVC, vea la guía [Overview of ASP.NET Core MVC](/aspnet/core/mvc/overview) (Introducción a MVC de ASP.NET Core).

Para agregar un controlador, haga lo siguiente:

1. Haga clic con el botón derecho en el nombre del proyecto y seleccione **Agregar > New Files** (Nuevos archivos). Seleccione **General > Clase vacía** y escriba un nombre de controlador:

    ![Cuadro de diálogo Nuevo archivo](media/asp-net-core-image8.png)

2. Agregue el código siguiente al nuevo controlador:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Agregue la dependencia `Microsoft.AspNetCore.Mvc` al proyecto. Para ello, haga clic con el botón derecho en la carpeta **Dependencia** y seleccione **Agregar paquete…**

4. Use el cuadro de búsqueda para buscar la biblioteca de NuGet para `Microsoft.AspNetCore.Mvc` y seleccione **Agregar paquete**. Es posible que tarde unos minutos en instalarse y que se le pida que acepte varias licencias para las dependencias necesarias:

    ![Agregar NuGet](media/asp-net-core-image9.png)

5. En la clase Startup, quite la expresión lambda `app.Run` y establezca la lógica de enrutamiento de dirección URL usada por MVC para determinar qué código debe invocar para lo siguiente:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Asegúrese de quitar la expresión lambda `app.Run`, ya que invalidará la lógica de enrutamiento.

    MVC usa el formato siguiente para determinar qué código se ejecuta:

    `/[Controller]/[ActionName]/[Parameters]`

    Al agregar el fragmento de código anterior, le indica a la aplicación que use como valor predeterminado el controlador `HelloWorld` y el método de acción `Index`.

6. Agregue la llamada `services.AddMvc();` al método `ConfigureServices`, como se muestra a continuación:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    También puede pasar información de parámetros desde la dirección URL al controlador.

7. Agregue otro método a HelloWorldController, como se muestra a continuación:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Si ejecuta ahora la aplicación, debería abrir automáticamente el explorador:

    ![Aplicación en ejecución en el explorador](media/asp-net-core-image13.png)

9. Intente ir a `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (reemplace `xxxx` por el puerto correcto). Debería aparecer lo siguiente:

    ![Aplicación en ejecución en el explorador con argumentos](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Solución de problemas

Si necesita instalar .NET Core manualmente en Mac OS 10.12 (Sierra) y versiones posteriores, haga lo siguiente:

1. Antes de iniciar la instalación de .NET Core, asegúrese de que ha instalado la versión estable más reciente de todas las actualizaciones del sistema operativo. Para comprobarlo, vaya a la aplicación del App Store y seleccione la pestaña Actualizaciones.

2. Siga los pasos indicados en el [sitio de .NET Core](https://www.microsoft.com/net/core#macos).

Complete todos los pasos correctamente para asegurarse de que .NET Core se instala correctamente.

## <a name="summary"></a>Resumen

En esta guía, se le ha proporcionado una introducción a ASP.NET Core. Describe qué es, cuándo se usa y cómo se usa en Visual Studio para Mac.
Para obtener más información sobre los pasos siguientes, vea las guías que se indican a continuación:
- Documentos sobre [ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1#build-web-ui-and-web-apis-using-aspnet-core-mvc).
- [Creating Backend Services for Native Mobile Applications](/aspnet/core/mobile/native-mobile-backend) (Crear servicios back-end para aplicaciones móviles nativas), donde se muestra cómo compilar un servicio REST mediante ASP.NET Core para una aplicación de Xamarin.Forms.
- [Laboratorio práctico de ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]