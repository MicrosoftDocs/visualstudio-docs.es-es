---
title: Creación de aplicaciones en Visual Studio para Mac de ASP.NET Core
description: En este artículo se describe cómo empezar a trabajar con ASP.NET en Visual Studio para Mac, incluida la instalación y la creación de un nuevo proyecto.
author: asb3993
ms.author: amburns
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: fb70966dd24c4d22d473b552297a60ddebdce106
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836184"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Creación de aplicaciones en Visual Studio para Mac de ASP.NET Core 


ASP.NET Core es un marco de código abierto y multiplataforma para crear en la nube conectadas a internet aplicaciones modernas, como aplicaciones web y servicios, aplicaciones de IoT y back-ends móviles. Pueden ejecutar aplicaciones de ASP.NET Core en [.NET Core](https://www.microsoft.com/net/core/platform) o en los tiempos de ejecución de .NET Framework. Se diseñada para proporcionar un marco de desarrollo optimizado para las aplicaciones que se implementan en la nube o se ejecutan en local. Consta de componentes modulares con una sobrecarga mínima, por lo que retener flexibilidad al crear soluciones. Puede desarrollar y ejecutar las aplicaciones multiplataforma ASP.NET Core en Windows, Mac y Linux. ASP.NET Core es código abierto en [GitHub](https://github.com/aspnet/home).

En este laboratorio, creará y explorar una aplicación de ASP.NET Core con Visual Studio para Mac.

## <a name="objectives"></a>Objetivos


> [!div class="checklist"]
> * Crear una aplicación web de ASP.NET Core
> * Explorar la ASP.NET Core de hospedaje, configuración y el modelo de middleware
> * Depurar una aplicación web ASP.NET Core

## <a name="prerequisites"></a>Requisitos previos

- [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Público destinatario

Esta práctica está destinada a desarrolladores que están familiarizados con C#, aunque no se requiere la vasta experiencia.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Tarea 1: Crear una nueva aplicación de ASP.NET Core

1. Inicie **Visual Studio para Mac**.

2. Seleccione **Archivo > Nueva solución**.

3. Seleccione el **.NET Core > aplicación** categoría y el **aplicación Web ASP.NET Core (C#)** plantilla. Haga clic en **Siguiente**.

    ![](media/netcore-image1.png)

4. Escriba un nombre de **"CoreLab"** y haga clic en **crear** para crear el proyecto. Se tardará unos instantes en completarse.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Tarea 2: La solución de bicicleta de paseo

1. La plantilla predeterminada producirá una solución con un solo proyecto de ASP.NET Core denominado **CoreLab**. Expanda el nodo del proyecto para exponer su contenido.

    ![](media/netcore-image3.png)

2. Este proyecto sigue el paradigma de model-view-controller (MVC) para proporcionar una división clara de responsabilidades entre los datos (modelos), la presentación (vistas) y la funcionalidad (controladores). Abra el archivo **HomeController.cs** desde la carpeta **Controladores**.

    ![](media/netcore-image4.png)

3. El **HomeController** clase por convención: controla todas las solicitudes entrantes que empiezan por **/Home**. El **índice** método controla las solicitudes a la raíz del directorio (como http://site.com/Home) y otros métodos de controlan las solicitudes a su ruta de acceso con nombre según la convención, como **About()** controlar las solicitudes a **http://site.com/Home/About** . Por supuesto, esto es todo configurable. Una notable es que la **HomeController** es el controlador de forma predeterminada en un proyecto nuevo, por lo que se solicita a la raíz del sitio ( **http://site.com** ) irá a través de **Index()** de la **HomeController** al igual que las solicitudes a **http://site.com/Home** o **http://site.com/Home/Index** .

    ![](media/netcore-image5.png)

4. El proyecto también tiene un **vistas** carpeta que contiene otras carpetas que se asignan a cada controlador (además de uno para **Shared** vistas. Por ejemplo, el archivo CSHTML de la vista (una extensión de HTML) para la ruta de acceso **/Home/About** estaría en **Views/Home/About.cshtml**. Abra ese archivo.

    ![](media/netcore-image6.png)

5. En este archivo CSHTML se usa la sintaxis de Razor para representar HTML en función de una combinación de etiquetas estándar y C# en línea. Puede aprender más sobre esto en el [documentación en línea](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. La solución también contiene un **wwwroot** carpeta que será la raíz del sitio web. Puede colocar el contenido estático del sitio (como CSS, imágenes y bibliotecas de JavaScript) directamente en las rutas de acceso en las que quiera que esté cuando se implemente el sitio.

    ![](media/netcore-image8.png)

7. También hay una variedad de archivos de configuración que sirven para administrar el proyecto, sus paquetes y la aplicación en tiempo de ejecución. Por ejemplo, la [configuración](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) predeterminada de la aplicación se almacena en **appsettings.json**. Pero puede invalidar algunos o todos estos valores de forma individual en cada entorno, por ejemplo, proporcionando un archivo **appsettings.Development.json** para el entorno **Desarrollo**.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Tarea 3: Descripción de cómo se hospeda la aplicación

1. Desde **el Explorador de soluciones**, abra **Program.cs**. Este es el programa previo que se ejecutará la aplicación.

    ![](media/netcore-image10.png)

2. Aunque hay sólo dos líneas de código aquí, son importantes. Vamos a desglosar ellos. Primero, un nuevo **WebHostBuilder** se crea. Las aplicaciones de ASP.NET Core requieren un host en el que se va a ejecutar. Un host debe implementar la **IWebHost** interfaz, que expone colecciones de características y servicios, y un **iniciar** método. El host se crea normalmente con una instancia de un **WebHostBuilder**, que genera y devuelve un **WebHost** instancia. El **WebHost** hace referencia al servidor que va a controlar las solicitudes.

    ![](media/netcore-image11.png)

3. Mientras el **WebHostBuilder** es responsable de crear el host que se arranque el servidor de la aplicación, requiere proporcionar un servidor que implementa **IServer**. De forma predeterminada, se trata de  **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , un servidor web multiplataforma para ASP.NET Core se basa en **libuv**, que es una biblioteca de E/S asincrónica multiplataforma.

    ![](media/netcore-image12.png)

4. A continuación, se establece la raíz del contenido del servidor. Esto determina dónde busca archivos de contenido, como los archivos de vista de MVC. La raíz del contenido de forma predeterminada es la carpeta desde la que se ejecuta la aplicación.

    ![](media/netcore-image13.png)

5. Si la aplicación debe funcionar con el servidor web de Internet Information Services (IIS), el **UseIISIntegration** método debe llamarse como parte de la creación del host. Que esto no configura un servidor, como **UseKestrel** does. Para usar IIS con ASP.NET Core, debe especificar **UseKestrel** y **UseIISIntegration**. **Kestrel** está diseñado para ejecutarse detrás de un proxy y no se deben implementar directamente accesible desde internet. **UseIISIntegration** especifica IIS como el servidor proxy inverso, pero es solo es pertinente cuando se ejecuta en equipos que tengan IIS. Si implementa la aplicación para Windows, déjelo en. Tampoco viene mal en caso contrario.

    ![](media/netcore-image14.png)

6. Es una práctica más limpia para separar la carga de la configuración de la aplicación de arranque. Para hacerlo fácilmente **UseStartup** se llama para especificar que el **inicio** clase va a llamar para la carga de configuración y otras tareas de inicio, por ejemplo, insertar middleware en la canalización HTTP. Puede tener varios **UseStartup** llamadas con la expectativa de que cada uno de ellos sobrescribe la configuración anterior según sea necesario.

    ![](media/netcore-image15.png)

7. El último paso para crear el **IWebHost** consiste en llamar a **compilar**.

    ![](media/netcore-image16.png)

8. Mientras **IWebHost** las clases necesarias para implementar el sin bloqueo **iniciar**, proyectos de ASP.NET Core tienen un método de extensión denominado **ejecutar** que ajusta  **Iniciar** con bloqueo de código por lo que no es necesario impedir manualmente que el método salir inmediatamente.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Tarea 4: Ejecución y depuración de la aplicación

1. En **el Explorador de soluciones**, haga clic en el **CoreLab** nodo del proyecto y seleccione **opciones**.

    ![](media/netcore-image18.png)

2. El **opciones de proyecto** cuadro de diálogo incluye todo lo que necesita para ajustar cómo se compila y ejecuta la aplicación. Seleccione el **ejecutar > configuraciones > predeterminado** nodo desde el panel izquierdo.

3. Comprobar **ejecutar en consola externa** y desactive la opción **pausar salida de consola**. Normalmente la aplicación hospeda a sí mismo no tendría su consola visible, pero en su lugar, debería iniciar sus resultados a la **salida** pad. Para los fines de este laboratorio, se la mostraremos en una ventana independiente, aunque no es necesario hacerlo durante el desarrollo normal.

4. Haga clic en **Aceptar**.

    ![](media/netcore-image19.png)

5. Presione **F5** para compilar y ejecutar la aplicación. Como alternativa, puede seleccionar **ejecutar > Iniciar depuración**.

6. Visual Studio para Mac iniciará dos ventanas. La primera es una ventana de consola que proporciona una vista en la aplicación de servidor autohospedado.

    ![](media/netcore-image20.png)

7. El segundo es una ventana de exploración típicos para probar el sitio. Como el explorador sabe, esta aplicación podría hospedarse en cualquier lugar. Haga clic en **sobre** para ir a esa página.

    ![](media/netcore-image21.png)

8. Entre otras cosas, la página acerca de representa algún texto establecido en el controlador.

    ![](media/netcore-image22.png)

9. Permite mantener ambas ventanas de abrirán y vuelva a Visual Studio para Mac. Abra **Controllers/HomeController.cs** si todavía no está abierto.

    ![](media/netcore-image23.png)

10. Establezca un punto de interrupción en la primera línea del método **About**. Puede hacerlo haciendo clic en el margen o estableciendo el cursor en la línea y presione **F9**. Esta línea establece algunos datos de la colección **ViewData** que se representan en la página CSHTML en **Views/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Volver al explorador y actualice la página. Esto desencadenará el punto de interrupción en Visual Studio para Mac.

12. Mueva el mouse sobre el **ViewData** miembro para ver sus datos. También puede expandir sus miembros secundarios para ver los datos anidados.

    ![](media/netcore-image25.png)

13. Quite el punto de interrupción de la aplicación con el mismo método usado para agregarlo.

14. Abra **Views/Home/About.cshtml**.

15. Cambie el texto **"additional"** por **"changed"** y guarde el archivo.

    ![](media/netcore-image26.png)

16. Presione el **continuar** botón para continuar la ejecución.

    ![](media/netcore-image27.png)

17. Vuelva a la ventana del explorador para ver el texto actualizado. Este cambio puede realizarse en cualquier momento y no requiere necesariamente un punto de interrupción del depurador. Si no ve el cambio se reflejará inmediatamente, actualice el explorador.

    ![](media/netcore-image28.png)

18. Cierre la consola de ventana y aplicación de explorador de pruebas. Esto detendrá la depuración también.

## <a name="task-5-application-startup-configuration"></a>Tarea 5: Configuración de inicio de la aplicación

1. Desde **el Explorador de soluciones**, abra **Startup.cs**. Es posible que observe algunos subrayados ondulados rojos inicialmente como paquetes de NuGet se están restaurando en segundo plano y el compilador Roslyn es crear una imagen completa de las dependencias del proyecto.

    ![](media/netcore-image29.png)

2. Busque el **inicio** método. Esta sección define la configuración inicial de la aplicación y está densamente empaquetada. Vayamos por partes.

    ![](media/netcore-image30.png)

3. El método comienza mediante la inicialización de un **ConfigurationBuilder** y establecer su ruta de acceso base.

    ![](media/netcore-image31.png)

4. A continuación, carga un requiere **appsettings.json** archivo.

    ![](media/netcore-image32.png)

5. Después de eso, intenta cargar un específicos del entorno **appsettings.json** archivo, lo que podría invalidar la configuración existente. Por ejemplo, se trata de un proporcionado **appsettings. Development.JSON** archivo usado para ese entorno específico. Para obtener más información sobre la configuración en ASP.NET Core, visite [los documentos](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Por último, se agregan las variables de entorno para el generador de configuración y se compila y se establece para el uso de la configuración.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Tarea 6: Insertar middleware de aplicación

1. Busque el **configurar** método en el **inicio** clase. Esto es donde se configura el middleware para que se puede insertar en la canalización HTTP y usa para procesar cada solicitud al servidor. Aunque este método se llama solo una vez, el contenido de los métodos (como **UseStaticFiles**) se pueden ejecutar en cada solicitud.

    ![](media/netcore-image36.png)

2. También puede agregar middleware adicional que se ejecutan como parte de la canalización. Agregue el código siguiente después de **app. UseStaticFiles** para agregar automáticamente una **X prueba** encabezado a todas las respuestas salientes. IntelliSense le ayudará a completar el código a medida que escribe.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Presione **F5** para compilar y ejecutar el proyecto.

4. Podemos usar el explorador para inspeccionar los encabezados para comprobar que se han agregado. Las instrucciones siguientes sirven para Safari, pero puede hacer lo mismo [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) o [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Una vez que el explorador cargue el sitio, seleccione **Safari > Preferencias**.

6. En el **avanzadas** pestaña **mostrar el menú desarrollo en la barra de menús** y cerrar el cuadro de diálogo.

    ![](media/netcore-image37.png)

7. Seleccione **desarrollar > Mostrar los recursos de página**.

8. Actualice la ventana del explorador para que pueden realizar un seguimiento y analizar el tráfico y el contenido de las herramientas de desarrollador recién abierto.

9. La página HTML de localhost representada por el servidor será el elemento seleccionado de forma predeterminada.

    ![](media/netcore-image38.png)

10. Expanda el **sidebar detalles**.

    ![](media/netcore-image39.png)

11. Desplácese hasta la parte inferior de la barra lateral para ver el encabezado de respuesta que agregó anteriormente en el código.

    ![](media/netcore-image40.png)

12. Cierre la ventana del explorador y la consola si se cumplen.

## <a name="summary"></a>Resumen

En este laboratorio, ha aprendido cómo comenzar a desarrollar aplicaciones de ASP.NET Core con Visual Studio para Mac. Si desea explorar el desarrollo de una aplicación de base de datos de películas más completa, consulte el [empezar a trabajar con ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc) tutorial.
