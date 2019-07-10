---
title: Compilación de aplicaciones de ASP.NET Core en Visual Studio para Mac
description: En este artículo se describe cómo empezar a trabajar con ASP.NET en Visual Studio para Mac, incluida la instalación y la creación de un nuevo proyecto.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: f0a2e8433877b3eb61228a886280707f3b4a37fe
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693134"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Compilación de aplicaciones de ASP.NET Core en Visual Studio para Mac 

ASP.NET Core es un marco multiplataforma y de código abierto en el que se pueden crear modernas aplicaciones conectadas a Internet y basadas en la nube, por ejemplo, servicios y aplicaciones web, aplicaciones de IoT y back-end móviles. Las aplicaciones de ASP.NET Core se pueden ejecutar en [.NET Core](https://www.microsoft.com/net/core/platform) o en los runtime de .NET Framework. Se ha diseñado para proporcionar una plataforma de desarrollo optimizada para las aplicaciones que se implementan en la nube o se ejecutan en local. Consta de componentes modulares con una sobrecarga mínima, por lo que se conserva la flexibilidad a la hora de crear soluciones. Puede desarrollar y ejecutar las aplicaciones multiplataforma ASP.NET Core en Windows, Mac y Linux. ASP.NET Core es código abierto en [GitHub](https://github.com/aspnet/home).

En este laboratorio se va a crear y examinar una aplicación de ASP.NET Core con Visual Studio para Mac.

## <a name="objectives"></a>Objetivos

> [!div class="checklist"]
> * Crear una aplicación web de ASP.NET Core
> * Examinar el hospedaje, la configuración y el modelo de middleware de ASP.NET Core
> * Depurar una aplicación web de ASP.NET Core

## <a name="prerequisites"></a>Requisitos previos

- [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Destinatarios

Este laboratorio está destinado a desarrolladores familiarizados con C#, aunque no se requiere una experiencia profunda.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Tarea 1: Creación de una nueva aplicación de ASP.NET Core

1. Inicie **Visual Studio para Mac**.

2. Seleccione **Archivo > Nueva solución**.

3. Seleccione la categoría **.NET Core > Aplicación** y la plantilla **Aplicación web de ASP.NET Core (C#)** . Haga clic en **Siguiente**.

    ![](media/netcore-image1.png)

4. Escriba el nombre **"CoreLab"** y haga clic en **Crear** para crear el proyecto. Tarda un momento en finalizar.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Tarea 2: Examen de la solución

1. La plantilla predeterminada crea una solución con un solo proyecto de ASP.NET Core denominado **CoreLab**. Expanda el nodo del proyecto para exponer su contenido.

    ![](media/netcore-image3.png)

2. Este proyecto sigue el paradigma Modelo-Vista-Controlador (MVC) para proporcionar una división clara de responsabilidades entre los datos (modelos), la presentación (vistas) y la funcionalidad (controladores). Abra el archivo **HomeController.cs** desde la carpeta **Controladores**.

    ![](media/netcore-image4.png)

3. La clase **HomeController** por convención controla todas las solicitudes entrantes que empiezan por **/Home**. El método **Index** controla las solicitudes a la raíz del directorio (como `http://site.com/Home`) y otros métodos controlan las solicitudes a su ruta de acceso con nombre según la convención, como **About()** controla las solicitudes a `http://site.com/Home/About`. Por supuesto, todo esto es configurable. Algo a destacar es que **HomeController** es el controlador predeterminado de un proyecto nuevo, por lo que las solicitudes a la raíz del sitio (`http://site.com`) irían a través de **Index()** de **HomeController** al igual que las solicitudes a `http://site.com/Home` o `http://site.com/Home/Index`.

    ![](media/netcore-image5.png)

4. El proyecto también tiene una carpeta **Vistas** que contiene otras carpetas que se asignan a cada controlador (además de una para las vistas **compartidas**). Por ejemplo, el archivo CSHTML de la vista (una extensión de HTML) para la ruta de acceso **/Home/About** estaría en **Views/Home/About.cshtml**. Abra ese archivo.

    ![](media/netcore-image6.png)

5. En este archivo CSHTML se usa la sintaxis de Razor para representar HTML en función de una combinación de etiquetas estándar y C# en línea. Puede obtener más información al respecto en la [documentación en línea](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. La solución también contiene una carpeta **wwwroot** que es la raíz del sitio web. Puede colocar el contenido estático del sitio (como CSS, imágenes y bibliotecas de JavaScript) directamente en las rutas de acceso en las que quiera que esté cuando se implemente el sitio.

    ![](media/netcore-image8.png)

7. También hay una variedad de archivos de configuración que sirven para administrar el proyecto, sus paquetes y la aplicación en tiempo de ejecución. Por ejemplo, la [configuración](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) predeterminada de la aplicación se almacena en **appsettings.json**. Pero puede invalidar algunos o todos estos valores de forma individual en cada entorno, por ejemplo, proporcionando un archivo **appsettings.Development.json** para el entorno **Desarrollo**.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Tarea 3: Descripción de cómo se hospeda la aplicación

1. En el **Explorador de soluciones**, abra **Program.cs**. Este es el programa previo que va a ejecutar la aplicación.

    ![](media/netcore-image10.png)

2. Aunque hay solo dos líneas de código, son fundamentales. Vamos a desglosarlas. Primero se crea un nuevo elemento **WebHostBuilder**. Las aplicaciones de ASP.NET Core requieren un host en el que ejecutarse. Un host debe implementar la interfaz **IWebHost**, que expone colecciones de características y servicios, y un método **Start**. El host se suele crear con una instancia de **WebHostBuilder**, que compila y devuelve una instancia de **WebHost**. **WebHost** hace referencia al servidor que va a controlar las solicitudes.

    ![](media/netcore-image11.png)

3. Aunque **WebHostBuilder** es responsable de crear el host que va a arrancar el servidor de la aplicación, exige proporcionar un servidor que implemente **IServer**. De forma predeterminada, este es **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , un servidor web multiplataforma para ASP.NET Core basado en **libuv**, que es una biblioteca de E/S asincrónica multiplataforma.

    ![](media/netcore-image12.png)

4. Luego se establece la raíz de contenido del servidor. Esta determina dónde se buscan los archivos de contenido, como los archivos de vistas de MVC. La raíz de contenido predeterminada es la carpeta desde la que se ejecuta la aplicación.

    ![](media/netcore-image13.png)

5. Si la aplicación debe funcionar con el servidor web de Internet Information Services (IIS), se debe llamar al método **UseIISIntegration** como parte de la creación del host. Esto no configura un servidor, como hace **UseKestrel**. Para usar IIS con ASP.NET Core, debe especificar **UseKestrel** y **UseIISIntegration**. **Kestrel** está diseñado para ejecutarse detrás de un proxy y no se debe implementar directamente de cara a Internet. **UseIISIntegration** especifica IIS como servidor proxy inverso, pero solo es relevante cuando se ejecuta en equipos con IIS. Si implementa la aplicación en Windows, déjelo. Tampoco viene mal.

    ![](media/netcore-image14.png)

6. Un procedimiento más profesional consiste en separar la carga de configuración del arranque de la aplicación. Para hacerlo fácilmente, se llama a **UseStartup** para especificar que se va a llamar a la clase **Startup** para la carga de configuración y otras tareas de inicio, como insertar middleware en la canalización HTTP. Puede tener varias llamadas a **UseStartup** con la expectativa de que cada una de ellas sobrescriba la configuración anterior según sea necesario.

    ![](media/netcore-image15.png)

7. El último paso para crear **IWebHost** es llamar a **Build**.

    ![](media/netcore-image16.png)

8. Aunque las clases **IWebHost** son necesarias para implementar el método **Start** sin bloqueo, los proyectos de ASP.NET Core tienen un método de extensión denominado **Run** que ajusta **Start** con código de bloqueo para que no tenga que evitar manualmente que el método salga de inmediato.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Tarea 4: Ejecución y depuración de la aplicación

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto **CoreLab** y seleccione **Opciones**.

    ![](media/netcore-image18.png)

2. El cuadro de diálogo **Opciones del proyecto** incluye todo lo necesario para ajustar cómo se compila y ejecuta la aplicación. Seleccione el nodo **Ejecutar > Configuraciones > Predeterminado** en el panel izquierdo.

3. Active **Ejecutar en la consola externa** y desactive **Pausar salida de la consola**. Normalmente la aplicación autohospedada no tendría su consola visible, sino que registraría sus resultados en el panel **Salida**. Para los fines de este laboratorio, se muestra también en una ventana independiente, aunque no es necesario hacerlo durante el desarrollo normal.

4. Haga clic en **Aceptar**.

    ![](media/netcore-image19.png)

5. Presione **F5** para compilar y ejecutar la aplicación. También puede seleccionar **Ejecutar > Iniciar depuración**.

6. Visual Studio para Mac inicia dos ventanas. La primera es una ventana de consola que proporciona una vista de la aplicación de servidor autohospedada.

    ![](media/netcore-image20.png)

7. La segunda es una ventana de explorador típica para probar el sitio. Por lo que sabe el explorador, esta aplicación podría hospedarse en cualquier lugar. Haga clic en **Acerca de** para ir a esa página.

    ![](media/netcore-image21.png)

8. Entre otras cosas, la página Acerca de representa algún texto establecido en el controlador.

    ![](media/netcore-image22.png)

9. Mantenga abiertas ambas ventanas y vuelva a Visual Studio para Mac. Abra **Controllers/HomeController.cs** si todavía no está abierto.

    ![](media/netcore-image23.png)

10. Establezca un punto de interrupción en la primera línea del método **About**. Para ello, haga clic en el margen o establezca el cursor en la línea y presione **F9**. Esta línea establece algunos datos de la colección **ViewData** que se representan en la página CSHTML en **Views/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Vuelva al explorador y actualice la página Acerca de. Esto desencadena el punto de interrupción en Visual Studio para Mac.

12. Mantenga el mouse sobre el miembro **ViewData** para ver sus datos. También puede expandir sus miembros secundarios para ver los datos anidados.

    ![](media/netcore-image25.png)

13. Quite el punto de interrupción de la aplicación con el mismo método usado para agregarlo.

14. Abra **Views/Home/About.cshtml**.

15. Cambie el texto **"additional"** por **"changed"** y guarde el archivo.

    ![](media/netcore-image26.png)

16. Presione el botón **Continuar** para continuar con la ejecución.

    ![](media/netcore-image27.png)

17. Vuelva a la ventana del explorador para ver el texto actualizado. Este cambio puede realizarse en cualquier momento y no requiere necesariamente un punto de interrupción del depurador. Actualice el explorador si no ve el cambio reflejado de inmediato.

    ![](media/netcore-image28.png)

18. Cierre la ventana del explorador de prueba y la consola de la aplicación. Esto también detiene la depuración.

## <a name="task-5-application-startup-configuration"></a>Tarea 5: Configuración de inicio de la aplicación

1. En el **Explorador de soluciones**, abra **Startup.cs**. Es posible que inicialmente observe algunos subrayados ondulados rojos a medida que los paquetes NuGet se restauran en segundo plano y el compilador Roslyn crea una imagen completa de las dependencias del proyecto.

    ![](media/netcore-image29.png)

2. Busque el método **Startup**. Esta sección define la configuración inicial de la aplicación y tiene mucho contenido. Vamos a desglosarlo.

    ![](media/netcore-image30.png)

3. El método comienza por inicializar un elemento **ConfigurationBuilder** y establecer su ruta de acceso base.

    ![](media/netcore-image31.png)

4. Luego carga un archivo **appsettings.json** necesario.

    ![](media/netcore-image32.png)

5. Después de eso, intenta cargar un archivo **appsettings.json** específico del entorno, lo que sobrescribiría la configuración existente. Por ejemplo, este es un archivo **appsettings.Development.json** proporcionado que se usa para ese entorno específico. Para obtener más información sobre la configuración en ASP.NET Core, vea [los documentos](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Por último, se agregan las variables de entorno al generador de configuración y la configuración se compila y se establece para su uso.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Tarea 6: Inserción del middleware de la aplicación

1. Busque el método **Configure** de la clase **Startup**. Aquí es donde se configura el middleware para que se pueda insertar en la canalización HTTP y usar para procesar cada solicitud al servidor. Aunque a este método se le llama solo una vez, el contenido de los métodos (como **UseStaticFiles**) se puede ejecutar en cada solicitud.

    ![](media/netcore-image36.png)

2. También puede agregar middleware adicional para que se ejecute como parte de la canalización. Agregue el código siguiente después de **app.UseStaticFiles** para agregar automáticamente un encabezado **X-Test** a cada respuesta saliente. IntelliSense ayuda a completar el código a medida que se escribe.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Presione **F5** para compilar y ejecutar el proyecto.

4. Se puede usar el explorador para inspeccionar los encabezados a fin de comprobar que se han agregado. Las instrucciones siguientes son para Safari, pero se puede hacer lo mismo en [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) o [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Una vez que el explorador cargue el sitio, seleccione **Safari > Preferencias**.

6. En la pestaña **Avanzado**, active **Mostrar el menú Desarrollo en la barra de menús** y cierre el cuadro de diálogo.

    ![](media/netcore-image37.png)

7. Seleccione **Desarrollo > Mostrar recursos de la página**.

8. Actualice la ventana del explorador para que las herramientas de desarrollador recién abiertas puedan seguir y analizar el tráfico y el contenido.

9. La página HTML de localhost representada por el servidor es el elemento seleccionado de forma predeterminada.

    ![](media/netcore-image38.png)

10. Expanda la **barra lateral Detalles**.

    ![](media/netcore-image39.png)

11. Desplácese hasta la parte inferior de la barra lateral para ver el encabezado de respuesta agregado anteriormente al código.

    ![](media/netcore-image40.png)

12. Cierre la ventana del explorador y la consola cuando esté satisfecho.

## <a name="summary"></a>Resumen

En este laboratorio ha aprendido cómo empezar a desarrollar aplicaciones de ASP.NET Core con Visual Studio para Mac. Si quiere examinar el desarrollo de una aplicación de base de datos de películas más completa, vea el tutorial [Introducción a ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc).
