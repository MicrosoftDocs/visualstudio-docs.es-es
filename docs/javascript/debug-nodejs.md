---
title: Depurar una aplicación Node.js
description: Visual Studio admite la depuración de aplicaciones de Node.js.
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 6e0ba454a00fb2cebdfaa8ba5fdba63ef3ed2748
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955898"
---
# <a name="debug-a-nodejs-app-in-visual-studio"></a>Depurar una aplicación Node.js en Visual Studio

Puede depurar código JavaScript y TypeScript con Visual Studio. Puede establecer y alcanzar puntos de interrupción, asociar el depurador, inspeccionar variables, ver la pila de llamadas y usar otras características de depuración.

## <a name="debug-server-side-script"></a>Depurar scripts del servidor

1. Con el proyecto abierto en Visual Studio, abra un archivo JavaScript del servidor (como *server.js*) y haga clic en el medianil hacia el medianil izquierdo para establecer un punto de interrupción:

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

1. Para ejecutar la aplicación, presione **F5** (**Depurar** > **Iniciar depuración**).

    El depurador se detiene en el punto de interrupción establecido (la instrucción actual está marcada en amarillo). Ahora, puede inspeccionar el estado de la aplicación desplazando el puntero sobre las variables que están actualmente en el ámbito, con ventanas del depurador como **Locales** e **Inspección**.

1. Presione **F5** para continuar la aplicación.

1. Si quiere utilizar las herramientas de desarrollo de Chrome o Herramientas de F12, presione **F12**. Puede usar estas herramientas para examinar el DOM e interactuar con la aplicación mediante la consola de JavaScript.

## <a name="debug-client-side-script"></a>Depurar scripts de cliente

Visual Studio admite la depuración de Internet Explorer y Chrome únicamente. En algunos escenarios, el depurador alcanza automáticamente los puntos de interrupción en los códigos JavaScript y TypeScript y en scripts insertados en archivos HTML.

Si el origen se han minimizado o creado mediante un transcompilador como TypeScript o Babel, será necesario recurrir a [asignaciones de origen](#generate_sourcemaps) para lograr la mejor experiencia de depuración. Sin los mapas de origen, el depurador se puede seguir asociando a un script de cliente en ejecución, pero solo podrá establecer y alcanzar puntos de interrupción en el archivo minimizado o transcompilado, no en el archivo de origen. Por ejemplo, en una aplicación Vue.js, el script minimizado se pasa como una cadena a una instrucción `eval`, y no hay ninguna manera de recorrer este código de forma efectiva con el depurador de Visual Studio, a menos que se usen mapas de origen. En algunos escenarios de depuración complejos, también se podrían usar las herramientas de desarrollo de Chrome o Herramientas de F12 para Microsoft Edge.

Para asociar el depurador desde Visual Studio y alcanzar puntos de interrupción en el código del cliente, el depurador suele necesitar ayuda para identificar el proceso correcto. Esta es una forma de habilitar esta opción con Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Asociar el depurador al script de cliente con Chrome

1. Cierre todas las ventanas de Chrome.

    Esto es necesario para poder ejecutar Chrome en el modo de depuración.

2. Abra el comando **Ejecutar** desde el botón **Inicio** de Windows (haga clic con el botón derecho y elija **Ejecutar**) y escriba el comando siguiente:

    `chrome.exe --remote-debugging-port=9222`

    Este comando inicia Chrome con la depuración habilitada.

3. Cambie a Visual Studio y establezca un punto de interrupción en el código fuente (establezca el punto de interrupción en una línea de código que permita los puntos de interrupción, como una instrucción `return` o una declaración `var`).

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Si necesita encontrar un código en particular en un archivo generado de gran tamaño, use **Ctrl**+**F** (**Editar** > **Buscar y reemplazar**  > **Búsqueda rápida**).

4. Con Chrome seleccionado como destino de depuración en Visual Studio, presione **Ctrl**+**F5** (**Depurar** > **Iniciar sin depurar**) para ejecutar la aplicación en el explorador.

    La aplicación se abre en una nueva pestaña del explorador.

    Si Chrome está disponible en la máquina, pero no aparece como opción, elija **Explorar con** en la lista desplegable de destino de depuración y seleccione Chrome como el destino de explorador predeterminado (elija **Establecer como predeterminado**).

5. Elija **Depurar** > **Asociar al proceso**.

6. En el cuadro de diálogo **Asociar al proceso**, elija **Código WebKit** en el campo **Asociar a** y escriba **chrome** en el cuadro de filtro para filtrar los resultados de la búsqueda.

    **Código WebKit** es el valor necesario con Chrome, que es un explorador basado en WebKit.

7. Seleccione el proceso de Chrome con el puerto de host correcto (1337 en esta imagen) y haga clic en **Asociar**.

    ![Asociar al proceso](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Sabrá que el depurador se ha asociado correctamente cuando el Explorador DOM y la Consola de JavaScript se abran correctamente en Visual Studio. Estas herramientas de depuración son similares a las herramientas de desarrollo de Chrome y a Herramientas F12 para Microsoft Edge.

    > [!NOTE]
    > Si el depurador no se conecta y aparece el mensaje "No se puede asociar al proceso. Existe una operación que no es legal en el estado actual", utilice el Administrador de tareas para cerrar todas las instancias de Chrome antes de iniciar Chrome en modo de depuración. Es posible que las extensiones de Chrome se estén ejecutando y eviten el modo de depuración completa.

8. Si el código con el punto de interrupción ya se ha ejecutado, actualice la página del explorador para alcanzar el punto de interrupción.

    Mientras está en pausa en el depurador, puede pasar el mouse sobre las variables y usar las ventanas del depurador para examinar el estado de la aplicación. Para avanzar el depurador, puede ejecutar el código paso a paso (**F5**, **F10** y **F11**).

    En el caso del código JavaScript minimizado o transcompilado, puede alcanzar el punto de interrupción ya sea en el código JavaScript transcompilado o en su ubicación asignada correspondiente en el archivo TypeScript (mediante mapas de origen), según cuál sea el estado del entorno y del explorador. En cualquier caso, puede ejecutar paso a paso el código y examinar las variables.

    * Si tiene que interrumpir el código en un archivo TypeScript y no puede hacerlo, use **Asociar al proceso** (tal y como se describe en los pasos anteriores) para asociar el depurador. Luego, abra el archivo TypeScript generado dinámicamente desde el Explorador de soluciones; para ello, abra **Documentos de Script** > **nombreDeArchivo.tsx**, establezca un punto de interrupción y actualice la página en el explorador (establezca el punto de interrupción en una línea de código que permita puntos de interrupción, como la instrucción `return` o una declaración `var`).

        Como alternativa, si tiene que interrumpir el código en un archivo TypeScript y no puede hacerlo, intente utilizar la instrucción `debugger;` en el archivo TypeScript o, en su lugar, establezca puntos de interrupción en las herramientas de desarrollo de Chrome.

    * Si tiene que interrumpir el código en un archivo JavaScript transcompilado (por ejemplo, *app-bundle.js*) y no puede hacerlo, quite el archivo de mapa de origen, *nombreDeArchivo.js.map*.

     > [!TIP]
     > Una vez que se asocia al proceso la primera vez siguiendo estos pasos, puede volver a asociar rápidamente al mismo proceso en Visual Studio 2017 si selecciona **Depurar** > **Reasociar al proceso**.

## <a name="generate_sourcemaps"></a> Generar mapas de origen para la depuración

Visual Studio tiene la capacidad de usar y generar mapas de origen en archivos de código fuente de JavaScript. Esto suele ser necesario cuando el origen se ha minimizado o creado mediante un transcompilador como TypeScript o Babel. Las opciones disponibles dependen del tipo de proyecto.

* Un proyecto de TypeScript en Visual Studio genera mapas de origen de forma automática y predeterminada.

* En un proyecto de JavaScript, deberá generar mapas de origen mediante un software que instala varios programas como webpack y un compilador como TypeScript (o Babel), que puede agregar al proyecto. En el caso del compilador de TypeScript, también deberá agregar un archivo *tsconfig.json*. Para obtener un ejemplo que muestra cómo llevar esto a cabo mediante una configuración de webpack básica, vea [Creación de una aplicación Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Si no está familiarizado con los mapas de origen, lea [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Introducción a los mapas de origen de JavaScript) antes de continuar.

Para configurar opciones avanzadas de mapas de origen, utilice un archivo *tsconfig.json* o la configuración del proyecto en un proyecto de TypeScript, pero no ambos.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Configurar mapas de origen con un archivo tsconfig.json

Si agrega un archivo *tsconfig.json* al proyecto, Visual Studio trata la raíz del directorio como un proyecto de TypeScript. Para agregar el archivo, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y, luego, elija **Agregar > Nuevo elemento > Web > Scripts > Archivo de configuración JSON de TypeScript**. Un archivo *tsconfig.json* como este de aquí se agregará al proyecto.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Opciones del compilador para tsconfig.json

* **inlineSourceMap**: emite un solo archivo con mapas de origen en lugar de crear un mapa de origen individual por cada archivo de origen.
* **inlineSources**: emite el origen junto con los mapas de origen dentro de un mismo archivo. Requiere que se establezca *inlineSourceMap* o *sourceMap*.
* **mapRoot**: especifica la ubicación donde el depurador debe encontrar los archivos de mapa de origen (*.map*) en lugar de la ubicación predeterminada. Use esta marca si los archivos *.map* en tiempo de ejecución deben estar en una ubicación diferente a la de los archivos *.js*. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación de los archivos *.map*.
* **sourceMap**: genera el archivo *.map* correspondiente.
* **sourceRoot**: especifica la ubicación en la que el depurador debe encontrar los archivos TypeScript en lugar de las ubicaciones de origen. Use esta marca si los orígenes en tiempo de ejecución deben estar en una ubicación diferente a la ubicación en tiempo de diseño. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de origen.

Para obtener más detalles sobre las opciones del compilador, eche un vistazo a la página [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html) (Opciones del compilador) en el manual de TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Configurar mapas de origen con la configuración del proyecto

La configuración de los mapas de origen también se puede establecer mediante las propiedades del proyecto, haciendo clic con el botón derecho en el proyecto y eligiendo **Proyecto > Propiedades > Compilación de TypeScript > Depuración**.

Encontrará disponibles estas opciones de proyecto.

* **Generar mapas de origen** (equivalente a **sourceMap** en *tsconfig.json*): genera el archivo *.map* correspondiente.
* **Especificar el directorio raíz de los mapas de origen** (equivalente a **mapRoot** en *tsconfig.json*): especifica la ubicación en la que el depurador debe encontrar los archivos de mapa en lugar de las ubicaciones generadas. Use esta marca si los archivos *.map* en tiempo de ejecución deben estar en una ubicación diferente a la de los archivos .js. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de mapa.
* **Especificar el directorio raíz de los archivos TypeScript** (equivalente a **sourceRoot** en *tsconfig.json*): especifica la ubicación en la que el depurador debe encontrar los archivos TypeScript en lugar de las ubicaciones de origen. Use esta marca si los archivos de origen en tiempo de ejecución deben estar en una ubicación diferente a la ubicación en tiempo de diseño. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de origen.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Depurar JavaScript en archivos dinámicos con Razor (ASP.NET)

Visual Studio admite la depuración de Internet Explorer y Chrome únicamente. Asociará automáticamente puntos de interrupción a los scripts insertados y de JavaScript/TypeScript en los archivos HTML.

La depuración de archivos generados dinámicamente no es automática. Los puntos de interrupción no se pueden alcanzar automáticamente en los archivos generados con sintaxis de Razor (cshtml, vbhtml). Para depurar este tipo de archivos, se pueden utilizar dos métodos:

* **Colocar la instrucción `debugger;` donde quiera realizar la interrupción**: esto hace que el script dinámico detenga la ejecución e inicie la depuración inmediatamente mientras se está creando.
* **Cargar la página y abrir el documento dinámico en Visual Studio**: para que este método funcione, deberá abrir el archivo dinámico durante la depuración, establecer el punto de interrupción y actualizar la página. Dependiendo de si usa Chrome o Internet Explorer, encontrará el archivo mediante una de las estrategias siguientes:

   En Chrome, vaya a **Explorador de soluciones > Documentos de Script > nombreDeLaPágina**.

    > [!NOTE]
    > Si usa Chrome, podría aparecer el mensaje `no source is available between `<script>` tags.` This is OK, just continue debugging.

   En Internet Explorer, vaya a **Explorador de soluciones > Documentos de Script > Windows Internet Explorer > nombreDeLaPágina**.

Para más información, vea [Client-side debugging of ASP.NET projects in Google Chrome](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Depuración del lado cliente de proyectos de ASP.NET en Google Chrome).
