---
title: Crear una aplicación ASP.NET Core con TypeScript
description: En este tutorial, creará una aplicación con ASP.NET Core y TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988556"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Tutorial: Crear una aplicación ASP.NET Core con TypeScript en Visual Studio

En este tutorial para TypeScript y ASP.NET Core de desarrollo de Visual Studio, creará una aplicación web sencilla, agregará código de TypeScript y, a continuación, ejecutará la aplicación. 

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

En este tutorial aprenderá a:
> [!div class="checklist"]
> * Crear un proyecto de ASP.NET Core
> * Agregar el paquete NuGet para la compatibilidad con TypeScript
> * Agregar código de TypeScript
> * Ejecutar la aplicación
> * Agregar una biblioteca de terceros mediante npm

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la carga de trabajo Desarrollo web y ASP.NET.

    ::: moniker range=">=vs-2019"
    Si todavía no ha instalado Visual Studio 2019, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si todavía no ha instalado Visual Studio 2017, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Creación de un nuevo proyecto MVC ASP.NET Core

Visual Studio administra los archivos de una aplicación en un *proyecto*. El proyecto incluye código fuente, recursos y archivos de configuración.

>[!NOTE]
> Para empezar con un proyecto de ASP.NET Core vacío y agregar un front-end de TypeScript, vea [ASP.NET Core con TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) en su lugar.

En este tutorial, empezará con un proyecto simple que contiene el código de una aplicación ASP.NET Core MVC.

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana de inicio**. En la ventana de inicio, elija **Crear un proyecto nuevo**. En la lista desplegable Lenguaje, elija **C#** . En el cuadro de búsqueda, escriba **ASP.NET** y, luego, elija **Aplicación web ASP.NET Core**. Seleccione **Siguiente**.

    Escriba un nombre para el proyecto y elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y luego elija **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core: C#** y después elija **Aceptar**.
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación web ASP.NET Core**, debe agregar la carga de trabajo **Desarrollo de ASP.NET y web**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

1. En el cuadro de diálogo que aparece, seleccione **Aplicación web (Modelo-Vista-Controlador)** y, después, elija **Crear** (o **Aceptar**).

   ![Elección de la plantilla de MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio crea la solución y abre el proyecto en el panel derecho.

## <a name="add-some-code"></a>Agregar algo de código

1. en el Explorador de soluciones (panel derecho). Haga clic con el botón derecho en el nodo de proyecto y elija **Administrar paquetes NuGet**. En la pestaña **Examinar**, busque **Microsoft.TypeScript.MSBuild** y, a continuación, haga clic en **Instalar** a la derecha para instalar el paquete.

   ![Adición del paquete NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio agrega el paquete NuGet en el nodo **Dependencias** del Explorador de soluciones.

   > [!NOTE]
   > Este tutorial requiere el paquete NuGet. Como alternativa, en sus propias aplicaciones, es posible que desee usar el [paquete npm de TypeScript](https://www.npmjs.com/package/typescript).

1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo de proyecto y elija **Agregar > Nueva carpeta**. Use el nombre *scripts* para la nueva carpeta.

1. Haga clic con el botón derecho en la carpeta *scripts* y elija **Agregar > Nuevo elemento**. Elija el **archivo de configuración JSON de TypeScript** y, a continuación, haga clic en **Agregar**.

   Visual Studio agrega el archivo *tsconfig.json* a la carpeta *scripts*. Puede usar este archivo para [configurar opciones](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) para el compilador de TypeScript.

1. Abra *tsconfig.json* y reemplace el código predeterminado por el siguiente código:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   La opción *outDir* especifica la carpeta de salida para los archivos de JavaScript del plan que transpila el compilador de TypeScript.

   Esta configuración proporciona una introducción básica al uso de TypeScript. En otros escenarios, por ejemplo, al usar [gulp o webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), es posible que desee una ubicación intermedia diferente para los archivos de JavaScript transpilados, dependiendo de sus herramientas y preferencias de configuración, en lugar de *../wwwroot/js*.

1. Haga clic con el botón derecho en la carpeta *scripts* y elija **Agregar > Nuevo elemento**. Elija el **archivo TypeScript**, escriba el nombre *app.ts* para el nombre de archivo y, a continuación, haga clic en **Agregar**.

   Visual Studio agrega *app.ts* a la carpeta *scripts*.

1. Abra *app.ts* y agregue el siguiente código de TypeScript.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio proporciona compatibilidad de IntelliSense con su código de TypeScript.

    Para probarlo, quite `.lastName` de la función `greeter` y, a continuación, vuelva a escribir "." y verá IntelliSense.

    ![Visualización de IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Seleccione `lastName` para volver a agregar el último nombre al código.

1. Abra la carpeta *Views/Home* y, a continuación, abra *index.html*.

1. Agregue el siguiente código HTML al final del archivo.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Abra la carpeta *Views/Shared* y, a continuación, abra *_Layout.cshtml*.

1. Agregue la siguiente referencia de script antes de la llamada a `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilar la aplicación

1. Elija **Compilar > Compilar solución**.

   Aunque la aplicación se compila automáticamente cuando la ejecuta, queremos fijarnos en algo que ocurre durante el proceso de compilación.

1. Abra la carpeta *wwwroot/js* y encontrará dos nuevos archivos, *app.js* y el archivo de asignación de origen, *app.js.map*. El compilador de TypeScript genera estos archivos.

   Los archivos de asignación de origen son necesarios para la depuración.

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **F5** (**Depurar** > **Iniciar depuración**) para ejecutar la aplicación.

    La aplicación se abre en un explorador.

    En la ventana del explorador, verá el encabezado **Bienvenido** y el botón **Hacer clic aquí**.

    ![ASP.NET Core con TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Haga clic en el botón para mostrar el mensaje que especificamos en el archivo TypeScript.

## <a name="debug-the-application"></a>Depurar la aplicación

1. Establezca un punto de interrupción en la función `greeter` de `app.ts` haciendo clic en el margen izquierdo del editor de código.

    ![Establecer un punto de interrupción](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Presione **F5** para ejecutar la aplicación.

   Es posible que tenga que responder a un mensaje para habilitar la depuración de scripts.

   La aplicación se pone en pausa en el punto de interrupción. Ahora, puede inspeccionar variables y usar características del depurador.

## <a name="add-typescript-support-for-a-third-party-library"></a>Incorporación de compatibilidad con TypeScript para una biblioteca de terceros

1. Siga las instrucciones de la [administración de paquetes de npm](../javascript/npm-package-management.md#aspnet-core-projects) para agregar un archivo `package.json` al proyecto. Esto agrega compatibilidad con npm al proyecto.

   >[!NOTE]
   > En el caso de los proyectos de ASP.NET Core, también se puede usar el [Administrador de bibliotecas](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) o yarn, en lugar de npm, para instalar los archivos JavaScript y CSS del lado cliente.

1. En este ejemplo, agregue un archivo de definición de TypeScript para jQuery al proyecto. Incluya lo siguiente en el archivo *package.json*.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Esto agrega compatibilidad con TypeScript para jQuery. La propia biblioteca de jQuery ya está incluida en la plantilla de proyecto de MVC (busque en wwwroot/lib en el Explorador de soluciones). Si se usa una plantilla distinta, es posible que también tenga que incluir el paquete de npm jQuery.

1. Si no el paquete está instalado en el Explorador de soluciones, haga clic con el botón derecho en el nodo de npm y elija **Restaurar paquetes**.

   >[!NOTE]
   > En algunos escenarios, el Explorador de soluciones puede indicar que un paquete de npm no está sincronizado con *package.json* debido a una incidencia conocida descrita [aquí](https://github.com/aspnet/Tooling/issues/479). Por ejemplo, es posible que el paquete aparezca como no instalado cuando sí que lo está. En la mayoría de los casos, se puede actualizar el Explorador de soluciones eliminando *package.json*, reiniciando Visual Studio y agregando de nuevo el archivo *package.json*, tal como se ha descrito anteriormente en este artículo.

1. En el Explorador de soluciones, haga clic con el botón derecho en la carpeta scripts y elija **Agregar** > **Nuevo elemento**.

1. Elija **Archivo TypeScript**, escriba *library.ts* y elija **Agregar**.

1. En *library.ts*, agregue el código siguiente.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Para facilitar las cosas, este código muestra un mensaje mediante jQuery y una alerta.

   Con las definiciones de tipo TypeScript para jQuery agregadas, se obtendrá compatibilidad con IntelliSense en objetos de jQuery cuando se escriba un signo "." después de un objeto jQuery, tal como se muestra aquí.

   ![IntelliSense de jQuery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. En _Layout.cshtml, actualice las referencias de script para incluir `library.js`.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. En Index.cshtml, agregue el código HTML siguiente al final del archivo.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Presione **F5** (**Depurar** > **Iniciar depuración**) para ejecutar la aplicación.

    La aplicación se abre en el explorador.

    Haga clic en **Aceptar** en la alerta para ver la página actualizada a **Versión de jQuery: 3.3.1!!** .

    ![Ejemplo de jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Pasos siguientes

Es posible que desee obtener más detalles sobre cómo usar TypeScript con ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core y TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
