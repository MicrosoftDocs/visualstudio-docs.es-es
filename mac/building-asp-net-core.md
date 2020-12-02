---
title: Compilación de aplicaciones ASP.NET Core
description: En este artículo se explica cómo crear y explorar las aplicaciones ASP.NET Core con Visual Studio para Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 22dfa4a33005afd64be54828f3b49c45244779d2
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189880"
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

    ![Captura de pantalla que muestra cómo seleccionar una plantilla de aplicación web para el nuevo proyecto.](media/netcore-image1.png)

4. Escriba el nombre **"CoreLab"** y haga clic en **Crear** para crear el proyecto. Tarda un momento en finalizar.

    ![Captura de pantalla de la configuración de la aplicación web, en la que se agrega un nombre de proyecto.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Tarea 2: Examen de la solución

1. La plantilla predeterminada crea una solución con un solo proyecto de ASP.NET Core denominado **CoreLab**. Expanda el nodo del proyecto para exponer su contenido.

    ![Captura de pantalla del nodo del proyecto de solución seleccionado para ver su contenido, incluidas las carpetas y los archivos.](media/netcore-image3.png)

2. Este proyecto sigue el paradigma Modelo-Vista-Controlador (MVC) para proporcionar una división clara de responsabilidades entre los datos (modelos), la presentación (vistas) y la funcionalidad (controladores). Abra el archivo **HomeController.cs** desde la carpeta **Controladores**.

    ![Captura de pantalla del proyecto de solución con una clase de C# seleccionada, denominada HomeController.](media/netcore-image4.png)

3. La clase **HomeController** por convención controla todas las solicitudes entrantes que empiezan por **/Home**. El método **Index** controla las solicitudes a la raíz del directorio (como `http://site.com/Home`) y otros métodos controlan las solicitudes a su ruta de acceso con nombre según la convención, como **About()** controla las solicitudes a `http://site.com/Home/About`. Por supuesto, todo esto es configurable. Algo a destacar es que **HomeController** es el controlador predeterminado de un proyecto nuevo, por lo que las solicitudes a la raíz del sitio (`http://site.com`) irían a través de **Index()** de **HomeController** al igual que las solicitudes a `http://site.com/Home` o `http://site.com/Home/Index`.

    ![Captura de pantalla de una clase de C# denominada HomeController.](media/netcore-image5.png)

4. El proyecto también tiene una carpeta **Vistas** que contiene otras carpetas que se asignan a cada controlador (además de una para las vistas **compartidas**). Por ejemplo, el archivo CSHTML de la vista (una extensión de HTML) para la ruta de acceso **/Home/About** estaría en **Views/Home/About.cshtml**. Abra ese archivo.

    ![Captura de pantalla de un proyecto de solución con el archivo C S H T M L seleccionado, denominado Acerca de.](media/netcore-image6.png)

5. En este archivo CSHTML se usa la sintaxis de Razor para representar HTML en función de una combinación de etiquetas estándar y C# en línea. Puede obtener más información al respecto en la [documentación en línea](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![Captura de pantalla de un archivo de C S H T M L que muestra sintaxis de Razor.](media/netcore-image7.png)

6. La solución también contiene una carpeta **wwwroot** que es la raíz del sitio web. Puede colocar el contenido estático del sitio (como CSS, imágenes y bibliotecas de JavaScript) directamente en las rutas de acceso en las que quiera que esté cuando se implemente el sitio.

    ![Captura de pantalla de una solución con la carpeta raíz w w w seleccionada.](media/netcore-image8.png)

7. También hay una variedad de archivos de configuración que sirven para administrar el proyecto, sus paquetes y la aplicación en tiempo de ejecución. Por ejemplo, la [configuración](/aspnet/core/fundamentals/configuration) predeterminada de la aplicación se almacena en **appsettings.json**. El archivo **appsettings.Development.json** está anidado bajo el archivo appsettings.json. En este caso, puede invalidar algunos o todos estos valores en cada entorno. Visual Studio para Mac anidará archivos de esta manera con la misma lógica que Visual Studio para Windows, de modo que los archivos a los que necesita tener acceso con más frecuencia estén en primer plano. 

    ![Captura de pantalla que muestra una vista detallada con un archivo JSON seleccionado.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Tarea 3: Descripción de cómo se hospeda la aplicación

1. En el **Explorador de soluciones**, abra **Program.cs**. Este es el programa previo que va a ejecutar la aplicación.

    ![Captura de pantalla de una solución con el archivo de código fuente de C# seleccionado, denominado Programa.](media/netcore-image10.png)

2. Aunque hay solo dos líneas de código, son fundamentales. Vamos a desglosarlas. Primero se crea un nuevo elemento **WebHostBuilder**. Las aplicaciones de ASP.NET Core requieren un host en el que ejecutarse. Un host debe implementar la interfaz **IWebHost**, que expone colecciones de características y servicios, y un método **Start**. El host se suele crear con una instancia de **WebHostBuilder**, que compila y devuelve una instancia de **WebHost**. **WebHost** hace referencia al servidor que va a controlar las solicitudes.

    ![Captura de pantalla del método Main de C# con una instrucción que inicializa una variable denominada host con el tipo WebHostBuilder.](media/netcore-image11.png)

3. Aunque **WebHostBuilder** es responsable de crear el host que va a arrancar el servidor de la aplicación, exige proporcionar un servidor que implemente **`IServer`** . De forma predeterminada, este es **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)**, un servidor web multiplataforma para ASP.NET Core basado en **libuv**, que es una biblioteca de E/S asincrónica multiplataforma.

    ![Captura de pantalla del método Main de C# donde se resalta la variable host que establece el servidor con el método UseKestrel.](media/netcore-image12.png)

4. Luego se establece la raíz de contenido del servidor. Esta determina dónde se buscan los archivos de contenido, como los archivos de vistas de MVC. La raíz de contenido predeterminada es la carpeta desde la que se ejecuta la aplicación.

    ![Captura de pantalla del método Main de C# donde se resalta la variable host que establece la raíz de contenido para el servidor con el método UseContentRoot.](media/netcore-image13.png)

5. Si la aplicación debe funcionar con el servidor web de Internet Information Services (IIS), se debe llamar al método **UseIISIntegration** como parte de la creación del host. Esto no configura un servidor, como hace **UseKestrel**. Para usar IIS con ASP.NET Core, debe especificar **UseKestrel** y **UseIISIntegration**. **Kestrel** está diseñado para ejecutarse detrás de un proxy y no se debe implementar directamente de cara a Internet. **UseIISIntegration** especifica IIS como servidor proxy inverso, pero solo es relevante cuando se ejecuta en equipos con IIS. Si implementa la aplicación en Windows, déjelo. Tampoco viene mal.

    ![Captura de pantalla del método Main de C# donde se resalta la variable host que establece el servidor proxy inverso con el método UseIISIntegration.](media/netcore-image14.png)

6. Un procedimiento más profesional consiste en separar la carga de configuración del arranque de la aplicación. Para hacerlo fácilmente, se llama a **UseStartup** para especificar que se va a llamar a la clase **Startup** para la carga de configuración y otras tareas de inicio, como insertar middleware en la canalización HTTP. Puede tener varias llamadas a **UseStartup** con la expectativa de que cada una de ellas sobrescriba la configuración anterior según sea necesario.

    ![Captura de pantalla del método Main de C# donde se resalta la variable host que establece la clase de inicio con la opción UseStartup.](media/netcore-image15.png)

7. El último paso para crear **IWebHost** es llamar a **Build**.

    ![Captura de pantalla del método Main de C# donde se resalta la variable de host con el método Build.](media/netcore-image16.png)

8. Aunque las clases **IWebHost** son necesarias para implementar el método **Start** sin bloqueo, los proyectos de ASP.NET Core tienen un método de extensión denominado **Run** que ajusta **Start** con código de bloqueo para que no tenga que evitar manualmente que el método salga de inmediato.

    ![Captura de pantalla del método Main de C# donde se resalta la instrucción host punto Run.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Tarea 4: Ejecución y depuración de la aplicación

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto **CoreLab** y seleccione **Opciones**.

    ![Captura de pantalla que muestra el menú contextual de la solución CoreLab, donde Opciones está resaltado.](media/netcore-image18.png)

2. El cuadro de diálogo **Opciones del proyecto** incluye todo lo necesario para ajustar cómo se compila y ejecuta la aplicación. Seleccione el nodo **Ejecutar > Configuraciones > Predeterminado** en el panel izquierdo.

3. Active **Ejecutar en la consola externa** y desactive **Pausar salida de la consola**. Normalmente, la aplicación autohospedada no tendría su consola visible, sino que registraría los resultados en la ventana **Salida**. Para los fines de este laboratorio, se muestra también en una ventana independiente, aunque no es necesario hacerlo durante el desarrollo normal.

4. Haga clic en **OK**.

    ![Captura de pantalla que muestra la pestaña Ejecutar configuración general, con Ejecutar en la consola externa seleccionado y Pausar salida de consola no seleccionado.](media/netcore-image19.png)

5. Presione **F5** para compilar y ejecutar la aplicación. También puede seleccionar **Ejecutar > Iniciar depuración**.

6. Visual Studio para Mac inicia dos ventanas. La primera es una ventana de consola que proporciona una vista de la aplicación de servidor autohospedada.

    ![Captura de pantalla que muestra la ventana de la consola de la aplicación de servidor autohospedado.](media/netcore-image20.png)

7. La segunda es una ventana de explorador típica para probar el sitio. Por lo que sabe el explorador, esta aplicación podría hospedarse en cualquier lugar. Haga clic en **Acerca de** para ir a esa página.

    ![Captura de pantalla que muestra una ventana del explorador para probar el sitio, donde se resalta la opción Acerca de.](media/netcore-image21.png)

8. Entre otras cosas, la página Acerca de representa algún texto establecido en el controlador.

    ![Captura de pantalla que muestra el resultado seleccionar la opción Acerca de, que es una página Acerca de.](media/netcore-image22.png)

9. Mantenga abiertas ambas ventanas y vuelva a Visual Studio para Mac. Abra **Controllers/HomeController.cs** si todavía no está abierto.

    ![Captura de pantalla que muestra la solución con la clase HomeController de C# seleccionada de nuevo.](media/netcore-image23.png)

10. Establezca un punto de interrupción en la primera línea del método **About**. Para ello, haga clic en el margen o establezca el cursor en la línea y presione **F9**. Esta línea establece algunos datos de la colección **ViewData** que se representan en la página CSHTML en **Views/Home/About.cshtml**.

    ![Captura de pantalla que muestra el método About con un punto de interrupción establecido.](media/netcore-image24.png)

11. Vuelva al explorador y actualice la página Acerca de. Esto desencadena el punto de interrupción en Visual Studio para Mac.

12. Mantenga el mouse sobre el miembro **ViewData** para ver sus datos. También puede expandir sus miembros secundarios para ver los datos anidados.

    ![Captura de pantalla que muestra un punto de interrupción con sus datos expandidos.](media/netcore-image25.png)

13. Quite el punto de interrupción de la aplicación con el mismo método usado para agregarlo.

14. Abra **Views/Home/About.cshtml**.

15. Cambie el texto **"additional"** por **"changed"** y guarde el archivo.

    ![Captura de pantalla del archivo C S H T M L denominado Acerca de con un cambio en el texto.](media/netcore-image26.png)

16. Presione el botón **Continuar** para continuar con la ejecución.

    ![Captura de pantalla de la ventana de Visual Studio que resalta el botón Continuar.](media/netcore-image27.png)

17. Vuelva a la ventana del explorador para ver el texto actualizado. Este cambio puede realizarse en cualquier momento y no requiere necesariamente un punto de interrupción del depurador. Actualice el explorador si no ve el cambio reflejado de inmediato.

    ![Captura de pantalla de la página Acerca de, esta vez con el texto cambiado.](media/netcore-image28.png)

18. Cierre la ventana del explorador de prueba y la consola de la aplicación. Esto también detiene la depuración.

## <a name="task-5-application-startup-configuration"></a>Tarea 5: Configuración de inicio de la aplicación

1. En el **Explorador de soluciones**, abra **Startup.cs**. Es posible que inicialmente observe algunos subrayados ondulados rojos a medida que los paquetes NuGet se restauran en segundo plano y el compilador Roslyn crea una imagen completa de las dependencias del proyecto.

    ![Captura de pantalla de la solución con el archivo de clase de C# seleccionado, denominado Startup.](media/netcore-image29.png)

2. Busque el método **Startup**. Esta sección define la configuración inicial de la aplicación y tiene mucho contenido. Vamos a desglosarla.

    ![Captura de pantalla que muestra el método Startup de la clase Startup.](media/netcore-image30.png)

3. El método comienza por inicializar un elemento **ConfigurationBuilder** y establecer su ruta de acceso base.

    ![Captura de pantalla del método Startup, que muestra una instrucción que Inicializa una variable denominada Builder con el tipo ConfigurationBuilder.](media/netcore-image31.png)

4. Luego carga un archivo **appsettings.json** necesario.

    ![Captura de pantalla del método Startup, que muestra la variable del generador usando el método AddJsonFile para agregar el archivo JSON denominado appSettings.](media/netcore-image32.png)

5. Después de eso, intenta cargar un archivo **appsettings.json** específico del entorno, lo que sobrescribiría la configuración existente. Por ejemplo, este es un archivo **appsettings.Development.json** proporcionado que se usa para ese entorno específico. Para obtener más información sobre la configuración en ASP.NET Core, vea [los documentos](/aspnet/core/fundamentals/configuration).

    ![Captura de pantalla del método Startup, que muestra la variable del generador usando el método AddJsonFile para agregar un archivo JSON específico del entorno denominado appSettings.](media/netcore-image34.png)

6. Por último, se agregan las variables de entorno al generador de configuración y la configuración se compila y se establece para su uso.

    ![Captura de pantalla del método Startup, que muestra la variable Builder que agrega variables de entorno luego usa el método Build para compilar la configuración.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Tarea 6: Inserción del middleware de la aplicación

1. Busque el método **Configure** de la clase **Startup**. Aquí es donde se configura el middleware para que se pueda insertar en la canalización HTTP y usar para procesar cada solicitud al servidor. Aunque a este método se le llama solo una vez, el contenido de los métodos (como **UseStaticFiles**) se puede ejecutar en cada solicitud.

    ![Captura de pantalla que muestra el método Configure de la clase Startup.](media/netcore-image36.png)

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

    ![Captura de pantalla que muestra el panel Opciones avanzadas del cuadro de diálogo Preferencias de Safari con la opción Mostrar el menú Desarrollar en la barra de menús seleccionada.](media/netcore-image37.png)

7. Seleccione **Desarrollo > Mostrar recursos de la página**.

8. Actualice la ventana del explorador para que las herramientas de desarrollador recién abiertas puedan seguir y analizar el tráfico y el contenido.

9. La página HTML de localhost representada por el servidor es el elemento seleccionado de forma predeterminada.

    ![Captura de pantalla que resalta la página H T M L localhost.](media/netcore-image38.png)

10. Expanda la **barra lateral Detalles**.

    ![Captura de pantalla que resalta el control que se va a usar para expandir la barra lateral Detalles.](media/netcore-image39.png)

11. Desplácese hasta la parte inferior de la barra lateral para ver el encabezado de respuesta agregado anteriormente al código.

    ![Captura de pantalla que resalta el encabezado de respuesta denominado XTest con un valor de Test.](media/netcore-image40.png)

12. Cierre la ventana del explorador y la consola cuando esté satisfecho.

## <a name="summary"></a>Resumen

En este laboratorio ha aprendido cómo empezar a desarrollar aplicaciones de ASP.NET Core con Visual Studio para Mac. Si quiere examinar el desarrollo de una aplicación de base de datos de películas más completa, vea el tutorial [Introducción a ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc).
