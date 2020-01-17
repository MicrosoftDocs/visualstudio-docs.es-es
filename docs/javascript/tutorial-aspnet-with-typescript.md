---
title: Crear una aplicación ASP.NET Core con TypeScript
description: En este tutorial, creará una aplicación con ASP.NET Core y TypeScript
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8d733c41e2833eeca2a8bf8c68f5e329f0af723c
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75681610"
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

En este tutorial, empezará con un proyecto simple que contiene el código de una aplicación ASP.NET Core MVC.

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **ASP.NET** y, luego, elija **Aplicación web ASP.NET Core: C#** . En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y elija **Node.js**. En el panel central, elija **Aplicación web ASP.NET Core: C#** y después elija **Aceptar**.
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación web ASP.NET Core**, debe agregar la carga de trabajo **Desarrollo de ASP.NET y web**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

1. Una vez que elija **Crear**, seleccione **Aplicación web (controlador de vista de modelos)** en el cuadro de diálogo y, a continuación, elija **Crear**.

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

## <a name="next-steps"></a>Pasos siguientes

Es posible que desee obtener más detalles sobre cómo usar TypeScript con ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core y TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
