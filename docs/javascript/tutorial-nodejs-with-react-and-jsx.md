---
title: Creación de una aplicación Node.js y React
description: En este tutorial, creará una aplicación con Node.js Tools para Visual Studio.
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f60cd71f1dda4e401acef1db9ccd8c5a0be2b961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "78235098"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Tutorial: Crear una aplicación Node.js y React en Visual Studio

Visual Studio permite crear fácilmente un proyecto de Node.js y usar IntelliSense y otras características integradas compatibles con Node.js. En este tutorial para Visual Studio, se crea un proyecto de aplicación web de Node.js a partir de una plantilla de Visual Studio. A continuación, se crea una aplicación sencilla con React.

En este tutorial aprenderá a:
> [!div class="checklist"]
> * Crear un proyecto de Node.js
> * Agregar paquetes de npm
> * Agregar código de React a la aplicación
> * Transpilar JSX
> * Asociar el depurador

## <a name="before-you-begin"></a>Antes de empezar

Esta es una sección rápida de P+F para presentar algunos conceptos clave.

### <a name="what-is-nodejs"></a>¿Qué es Node.js?

Node.js es un entorno de runtime de JavaScript para servidor que ejecuta JavaScript en el servidor.

### <a name="what-is-npm"></a>¿Qué es npm?

npm es el administrador de paquetes predeterminado de Node.js. El administrador de paquetes permite a los programadores publicar y compartir más fácilmente el código fuente de las bibliotecas de Node.js, y está diseñado para simplificar la instalación, la actualización y la desinstalación de bibliotecas.

### <a name="what-is-react"></a>¿Qué es React?

React es un marco front-end para crear una interfaz de usuario.

### <a name="what-is-jsx"></a>¿Qué es JSX?

JSX es una extensión de sintaxis de JavaScript que se suele usar con React para describir elementos de la interfaz de usuario. El código JSX debe transpilarse a JavaScript sin formato para que pueda ejecutarse en un explorador.

### <a name="what-is-webpack"></a>¿Qué es webpack?

webpack empaqueta archivos JavaScript para que puedan ejecutarse en un explorador. También puede transformar o empaquetar otros recursos y activos. A menudo se usa para especificar un compilador, como Babel o TypeScript, con el que transpilar código de JSX o TypeScript a JavaScript sin formato.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la carga de trabajo de desarrollo de Node.js.

    ::: moniker range=">=vs-2019"
    Si todavía no ha instalado Visual Studio 2019, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si todavía no ha instalado Visual Studio 2017, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

    ![Carga de trabajo Node.js en el instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Debe tener instalado el runtime de Node.js.

    Este tutorial se ha probado con la versión 10.16.0.

    Si no lo tiene instalado, se recomienda instalar la versión de LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/) para ofrecer una mejor compatibilidad con los marcos y las bibliotecas externos. Node.js se ha compilado para arquitecturas de 32 y 64 bits. Las herramientas de Node.js en Visual Studio, incluidas en la carga de trabajo de Node.js, admiten ambas versiones. Solo se requiere una y el instalador de Node.js solo admite que se instale una a la vez.
    
    En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta un entorno de ejecución instalado, puede configurar el proyecto para que haga referencia al entorno de ejecución instalado en la página de propiedades (después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto, elija **Propiedades** y establezca la **ruta de acceso de Node.exe**). Puede usar una instalación global de Node.js o puede especificar la ruta de acceso a un intérprete local en cada uno de los proyectos de Node.js. 

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, cree un proyecto de aplicación web de Node.js.

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **Node.js** y, a continuación, elija **Aplicación web en blanco de Node.js: JavaScript** (aunque en este tutorial se usa el compilador de TypeScript, los pasos requieren que empiece con la plantilla de **JavaScript**).
    
    En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y elija **Node.js**. En el panel central, elija **Aplicación web en blanco de Node.js**, escriba el nombre **NodejsWebAppBlank** y haga clic en **Aceptar**.
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación web en blanco de Node.js**, debe agregar la carga de trabajo **Desarrollo de Node.js**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

    Visual Studio crea la solución y abre el proyecto.

    ![Proyecto de Node.js en el Explorador de soluciones](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) El proyecto está resaltado en **negrita**. Tiene el nombre que le asignó en el cuadro de diálogo **Nuevo proyecto**. En el sistema de archivos, este proyecto se representa mediante un archivo *.njsproj* en la carpeta del proyecto. Para establecer propiedades y variables de entorno asociadas al proyecto, haga clic con el botón derecho en el proyecto y elija **Propiedades**. Puede hacer recorridos de ida y vuelta con otras herramientas de desarrollo, dado que el archivo de proyecto no realiza cambios personalizados en el origen del proyecto Node.js.

    (2) En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo *.sln* en el disco, es un contenedor para uno o más proyectos relacionados.

    (3) En el nodo npm se muestran todos los paquetes npm instalados. Puede hacer clic con el botón derecho en el nodo de npm para buscar e instalar paquetes de npm mediante un cuadro de diálogo, o instalar y actualizar los paquetes con la configuración de *package.json* y con las opciones que aparecen al hacer clic con el botón derecho en el nodo de npm.

    (4) *package.json* es un archivo usado por npm para administrar las dependencias y las versiones de los paquetes instalados localmente. Para obtener más información sobre este archivo, consulte [package.json configuration](../javascript/configure-packages-with-package-json.md) (Configuración de package.json).

    (5) Los archivos del proyecto como *server.js* se muestran en el nodo del proyecto. *server.js* es el archivo de inicio del proyecto, por lo que aparece en **negrita**. Puede establecer el archivo de inicio si hace clic con el botón derecho en un archivo del proyecto y selecciona **Establecer como archivo de inicio de Node.js**.

## <a name="add-npm-packages"></a>Agregar paquetes de npm

Esta aplicación requiere una serie de módulos de npm para ejecutarse correctamente.

* react
* react-dom
* express
* ruta de acceso
* ts-loader
* typescript
* webpack
* webpack-cli

1. En el Explorador de soluciones (panel derecho), haga clic con el botón derecho en el nodo **npm** del proyecto y elija **Instalar nuevos paquetes de NPM**.

    En el cuadro de diálogo **Instalar nuevos paquetes de NPM**, puede elegir instalar la versión más reciente del paquete o especificar una versión. Si decide instalar la versión actual de estos paquetes, pero experimenta errores inesperados más adelante, puede que necesite instalar las versiones exactas de paquete que se indican más adelante en estas instrucciones.

1. En el cuadro de diálogo **Instalar nuevos paquetes de NPM**, busque el paquete react y haga clic en **Instalar paquete** para instalarlo.

    ![Instalar paquetes de npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Haga clic en la ventana **Resultados** para ver el progreso en la instalación del paquete (seleccione **Npm** en el campo **Mostrar salida de**). Una vez instalado, el paquete aparece en el nodo **npm**.

    El archivo *package.json* del proyecto se actualiza con la nueva información de paquete, incluida su versión.

1. En lugar de usar la interfaz de usuario para buscar y agregar el resto de los paquetes de uno en uno, pegue el siguiente código en *package.json*. Para ello, agregue una sección `dependencies` con este código:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Si ya hay una sección `dependencies` en su versión de la plantilla en blanco, reemplácela por el código JSON anterior. Para más información sobre cómo usar este archivo, vea [Configuración de package.json](../javascript/configure-packages-with-package-json.md).

1. Guarde los cambios.

1. Haga clic con el botón derecho en el nodo **npm** del proyecto y seleccione **Actualizar los paquetes de NPM** .

    En el panel inferior, seleccione la ventana **Resultados** para ver el progreso de la instalación de los paquetes. La instalación puede tardar unos minutos y es posible que no vea los resultados inmediatamente. Para ver la salida, asegúrese de seleccionar **Npm** en el campo **Mostrar salida de** en la ventana **Salida**.

    Estos son los módulos npm tal y como aparecen en el Explorador de soluciones después de su instalación.

    ![paquetes npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Si prefiere instalar paquetes npm con la línea de comandos, haga clic con el botón derecho en el nodo del proyecto y seleccione **Abrir símbolo del sistema aquí**. Utilice los comandos estándar de Node.js para instalar los paquetes.

## <a name="add-project-files"></a>Agregar archivos de proyecto

En estos pasos, agregará cuatro nuevos archivos al proyecto.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Para esta sencilla aplicación, los nuevos archivos de proyecto se agregan en la raíz del proyecto. (Por lo general y en la mayoría de las aplicaciones, los archivos se agregan en las subcarpetas, ajustando en consecuencia las referencias de la ruta de acceso relativa).

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto **NodejsWebAppBlank** y elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, elija **Archivo JSX de TypeScript**, escriba el nombre *app.tsx* y seleccione **Agregar** o **Aceptar**.

1. Repita estos pasos para agregar *webpack-config.js*. En lugar de un archivo de TypeScript JSX, elija **Archivo JavaScript**.

1. Repita los mismos pasos para agregar *index.html* al proyecto. En lugar de un archivo JavaScript, elija **Archivo HTML**.

1. Repita los mismos pasos para agregar *tsconfig.json* al proyecto. En lugar de un archivo JavaScript, elija **Archivo de configuración JSON de TypeScript**.

## <a name="add-app-code"></a>Agregar código de aplicación

1. Abra *server.js* y reemplace el código existente por lo siguiente:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   El código anterior usa Express para iniciar Node.js como el servidor de aplicaciones web. Este código establece el puerto en el número de puerto que está configurado en las propiedades del proyecto (el valor predeterminado es 1337). Para abrir las propiedades del proyecto, haga clic con el botón derecho en el Explorador de soluciones y elija **Propiedades**.

1. Abra *app.tsx* y agregue el siguiente código:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    El código anterior usa la sintaxis JSX y React para mostrar un mensaje sencillo.

1. Abra *index.html* y reemplace la sección **body** por el siguiente código:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Esta página HTML carga *app-bundle.js*, que contiene el código JSX y React transpilado a JavaScript sin formato. Actualmente, *app-bundle.js* es un archivo vacío. En la sección siguiente, se configuran las opciones para transpilar el código.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configure las opciones de compilador de TypeScript y webpack

En los pasos anteriores, se agregó *webpack-config.js* al proyecto. A continuación, se agrega código de configuración de webpack. Se agrega una configuración de webpack simple que especifica un archivo de entrada (*app.tsx*) y un archivo de salida (*app-bundle.js*) para agrupar y transpilar JSX a JavaScript sin formato. Para transpilar, también se configuran algunas opciones del compilador TypeScript. Este código es una configuración básica que sirve como introducción al compilador TypeScript y webpack.

1. En el Explorador de soluciones, abra *webpack-config.js* y agregue el código siguiente.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    El código de configuración de webpack indica a Webpack que utilice el cargador de TypeScript para transcompilar el JSX.

1. Abra *tsconfig.json* y reemplace el código predeterminado por el código siguiente, que especifica las opciones del compilador TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* se especifica como el archivo de origen.

## <a name="transpile-the-jsx"></a>Transpilar el JSX

1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo del proyecto y elija **Abrir símbolo del sistema aquí**.

1. En el símbolo del sistema, escriba el siguiente comando:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    La ventana del símbolo del sistema muestra el resultado.

    ![Ejecutar webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Si ve algún error en lugar de la salida anterior, debe solucionarlo para que funcione la aplicación. Si las versiones del paquete npm son diferentes de las versiones que se muestran en este tutorial, esa puede ser una fuente de errores. Una manera de corregir errores es usar las versiones exactas que se muestran en los pasos anteriores. Además, si una o varias de estas versiones del paquete están en desuso y producen un error, deberá instalar una versión más reciente para corregir los errores. Para obtener información sobre cómo usar *package.json* para controlar las versiones del paquete de npm, consulte [package.json configuration](../javascript/configure-packages-with-package-json.md) (Configuración de package.json).

1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo del proyecto y elija **Agregar** > **Carpeta existente**; luego elija la carpeta *dist* y haga clic en **Seleccionar carpeta**.

    Visual Studio agrega la carpeta *dist* al proyecto, que contiene *app-bundle.js* y *app-bundle.js.map*.

1. Abra *app-bundle.js.* para ver el código de JavaScript transpilado.

1. Si se le pide que vuelva a cargar archivos modificados externamente, haga clic en **Sí a todo**.

    ![Cargar archivos modificados](../javascript/media/tutorial-nodejs-react-reload-files.png)

Cada vez que realice cambios en *app.tsx*, debe volver a ejecutar el comando webpack. Para automatizar este paso, agregue un script de compilación para transpilar el JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Agregar un script de compilación para transpilar el JSX

A partir de Visual Studio 2019, se requiere un script de compilación. En lugar de transpilar el JSX en la línea de comandos (como se muestra en la sección anterior), puede hacerlo al compilar desde Visual Studio.

* Abra *package.json* y agregue la siguiente sección después de la sección `dependencies`:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Ejecutar la aplicación

1. Seleccione Microsoft Edge o Chrome como destino de depuración actual.

    ::: moniker range=">=vs-2019"
    ![Seleccionar Chrome como destino de depuración](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Seleccionar Chrome como destino de depuración](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Si Chrome está disponible en el equipo, pero no aparece como opción, seleccione **Explorador web (nombre del explorador)** > **Seleccionar explorador web** en la lista desplegable de destino de depuración y seleccione **Chrome** como destino de explorador predeterminado.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si Chrome está disponible en el equipo, pero no aparece como opción, seleccione **Explorador web (nombre del explorador)** > **Google Chrome** en la lista desplegable de destino de depuración y seleccione **Chrome** como destino de explorador predeterminado.
    ::: moniker-end

1. Para ejecutar la aplicación, presione **F5** (**Depurar** > **Iniciar depuración**) o en el botón de flecha verde.

    Se abre una ventana de consola de Node.js que muestra el puerto en el que escucha el depurador.

    Visual Studio abre la aplicación con el archivo de inicio, *server.js*.

    ![Ejecutar React en el explorador](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Cierre la ventana del explorador.

1. Cierre la ventana de la consola.

## <a name="set-a-breakpoint-and-run-the-app"></a>Establecer un punto de interrupción y ejecutar la aplicación

1. En *server.js*, haga clic en el margen interno a la izquierda de la declaración `staticPath` para establecer un punto de interrupción:

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

1. Para ejecutar la aplicación, presione **F5** (**Depurar** > **Iniciar depuración**).

    El depurador se detiene en el punto de interrupción establecido (la instrucción actual está marcada en amarillo). Ahora, puede inspeccionar el estado de la aplicación desplazando el puntero sobre las variables que están actualmente en el ámbito, con ventanas del depurador como **Locales** e **Inspección**.

1. Presione **F5** para continuar la aplicación.

1. Si quiere usar las herramientas de desarrollo de Chrome o Herramientas de F12 para Microsoft Edge, presione **F12**. Puede usar estas herramientas para examinar el DOM e interactuar con la aplicación mediante la consola de JavaScript.

1. Cierre el explorador web y la consola.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Establecer y alcanzar un punto de interrupción en el código React del lado cliente

En la sección anterior se asoció el depurador al código Node.jse del lado servidor. Para asociar el depurador de Visual Studio y establecer puntos de interrupción en el código React del cliente, el depurador necesita ayuda para identificar el proceso correcto. Esta es una manera de habilitar esta opción.

### <a name="prepare-the-browser-for-debugging"></a>Preparación del explorador para la depuración

::: moniker range=">=vs-2019"
Para este escenario, use Microsoft Edge (Chromium), denominado actualmente **Microsoft Edge Beta** en el IDE, o bien Chrome.
::: moniker-end
::: moniker range="vs-2017"
Para este escenario, use Chrome.
::: moniker-end

1. Cierre todas las ventanas del explorador de destino.

   Otras instancias del explorador pueden impedir que el explorador se abra con la depuración habilitada. (Puede que las extensiones de explorador estén en ejecución e impidan el modo de depuración completa, por lo que es posible que tenga que abrir el Administrador de tareas para encontrar instancias inesperadas de Chrome).

   ::: moniker range=">=vs-2019"
   En el caso de Microsoft Edge (Chromium), cierre también todas las instancias de Chrome. Como los dos exploradores comparten el código base de Chromium, se obtiene el mejor resultado.
   ::: moniker-end

   ::: moniker range=">=vs-2019"
   En el caso de Microsoft Edge (Chromium), cierre también todas las instancias de Chrome. Como los dos exploradores usan el código base de chromium, se obtiene el mejor resultado.
   ::: moniker-end

2. Inicie el explorador con la depuración habilitada.

    ::: moniker range=">=vs-2019"
    A partir de Visual Studio 2019, puede establecer la marca `--remote-debugging-port=9222` al iniciar el explorador si selecciona **Explorar con...** > en la barra de herramientas **Depurar**, elige **Agregar** y, después, establece la marca en el campo **Argumentos**. Use otro nombre descriptivo para el explorador, como **Microsoft Edge con depuración** o **Chrome con depuración**. Para obtener información detallada, vea las [notas de la versión](/visualstudio/releases/2019/release-notes-v16.2).

    ![Establezca el explorador para que se abra con la depuración habilitada.](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Como alternativa, abra el comando **Ejecutar** desde el botón **Inicio** de Windows (haga clic con el botón derecho y elija **Ejecutar**), y escriba el comando siguiente:

    `msedge --remote-debugging-port=9222`

    o bien

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Abra el comando **Ejecutar** desde el botón **Inicio** de Windows (haga clic con el botón derecho y elija **Ejecutar**) y escriba el comando siguiente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Esto inicia el explorador con la depuración habilitada.

    La aplicación todavía no está en ejecución, por lo que se obtiene una página del explorador vacía.

### <a name="attach-the-debugger-to-client-side-script"></a>Asociación del depurador al script del lado cliente

1. Cambie a Visual Studio y, después, establezca un punto de interrupción en el código fuente, ya sea *app-bundle.js* o *app.tsx*.

    Para *app-bundle.js*, establezca el punto de interrupción en la función `render()`, como se muestra en la ilustración siguiente:

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Para buscar la función `render()` en el archivo *app-bundle.js* transpilado, presione **Ctrl**+**F** (**Editar** > **Buscar y reemplazar** > **Búsqueda rápida**).

    Para *app.tsx*, establezca el punto de interrupción dentro de la función `render()`, en la instrucción `return`.

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Si va a establecer el punto de interrupción en el archivo *.tsx* (en lugar de *app-bundle.js*), tendrá que actualizar *webpack-config.js*. Reemplace el código siguiente:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    con este código:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Se trata de una configuración solo de desarrollo para habilitar la depuración en Visual Studio. Esta configuración permite invalidar las referencias generadas en el archivo de mapa de origen, *app-bundle.js.map*, al compilar la aplicación. De forma predeterminada, las referencias a webpack en el archivo de mapa de origen incluyen el prefijo *webpack:///* , lo que impide que Visual Studio encuentre el archivo de origen, *app.tsx*. En concreto, cuando realiza este cambio, la referencia al archivo de origen, *app.tsx*, cambia de *webpack:///./app.tsx* a *./app.tsx*, lo que permite la depuración.

3. Seleccione el explorador de destino como destino de depuración en Visual Studio y después presione **Ctrl**+**F5** (**Depurar** > **Iniciar sin depurar**) para ejecutar la aplicación en el explorador.

    ::: moniker range=">=vs-2019"
    Si ha creado una configuración de explorador con un nombre descriptivo, elíjala como destino de depuración.
    ::: moniker-end

    La aplicación se abre en una nueva pestaña del explorador.

4. Elija **Depurar** > **Asociar al proceso**.

    > [!TIP]
    > A partir de Visual Studio 2017, una vez que se siguen estos pasos para asociar al proceso la primera vez, puede volver a asociar rápidamente al mismo proceso si selecciona **Depurar** > **Reasociar al proceso**.

5. En el cuadro de diálogo **Asociar al proceso**, obtendrá una lista filtrada de las instancias del explorador a las que se puede asociar.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, elija el depurador correcto para el explorador de destino, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** en el campo **Asociar a:** , escriba **chrome** o **edge** en el cuadro de filtro para filtrar los resultados de la búsqueda.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **Código WebKit** en el campo **Asociar a** y escriba **chrome** en el cuadro de filtro para filtrar los resultados de la búsqueda.
    ::: moniker-end

6. Seleccione el proceso de explorador con el puerto de host correcto (localhost en este ejemplo) y seleccione **Asociar**.

    Es posible que también aparezca el puerto (1337) en el campo **Título** para facilitar la selección de la instancia correcta del explorador.

    ::: moniker range=">=vs-2019"
    En el ejemplo siguiente se muestra qué aspecto tiene para el explorador Microsoft Edge (Chromium).

    ![Asociar al proceso](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Asociar al proceso](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Sabrá que el depurador se ha asociado correctamente cuando el Explorador DOM y la Consola de JavaScript se abran correctamente en Visual Studio. Estas herramientas de depuración son similares a las herramientas de desarrollo de Chrome y a Herramientas F12 para Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Si el depurador no se conecta y aparece el mensaje "No se puede asociar al proceso. Existe una operación que no es legal en el estado actual.", use el Administrador de tareas para cerrar todas las instancias del explorador de destino antes de iniciarlo en modo de depuración. Es posible que las extensiones del explorador estén en ejecución y eviten el modo de depuración completa.

7. Dado que el código ya se ejecuta con el punto de interrupción, actualice la página del explorador para alcanzar el punto de interrupción.

    Mientras está en pausa en el depurador, puede pasar el mouse sobre las variables y usar las ventanas del depurador para examinar el estado de la aplicación. Para avanzar el depurador, puede ejecutar el código paso a paso (**F5**, **F10** y **F11**). Para más información sobre las características de depuración básicas, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

    Puede alcanzar el punto de interrupción en el archivo *app-bundle.js* o en su ubicación asignada en *app.tsx*, en función de los pasos que haya seguido antes, junto con el estado del explorador y el entorno. En cualquier caso, puede ejecutar paso a paso el código y examinar las variables.

   * Si tiene que interrumpir el código en *app.tsx* y no puede hacerlo, use **Asociar al proceso** tal como se describe en los pasos anteriores para conectar el depurador. Asegúrese de que el entorno está configurado correctamente:

      * Ha cerrado todas las instancias del explorador, incluidas las extensiones de Chrome (mediante el Administrador de tareas), para que pueda ejecutar el explorador en modo de depuración. Asegúrese de iniciar el explorador en modo de depuración.

      * Asegúrese de que el archivo de mapa de origen incluye una referencia a *./app.tsx* y no a *webpack:///./app.tsx*, lo que impide que el depurador de Visual Studio encuentre *app.tsx*.
       Como alternativa, si tiene que interrumpir el código en un archivo *app.tsx* y no puede hacerlo, intente usar la instrucción `debugger;` de *app.tsx* o, en su lugar, establezca puntos de interrupción en las herramientas de desarrollo de Chrome (o las Herramientas de F12 para Microsoft Edge).

   * Si tiene que interrumpir el código en *app-bundle.js* y no puede hacerlo, quite el archivo de mapa de origen, *app-bundle.js.map*.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service](../javascript/publish-nodejs-app-azure.md) (Implementar la aplicación en App Service de Linux)
