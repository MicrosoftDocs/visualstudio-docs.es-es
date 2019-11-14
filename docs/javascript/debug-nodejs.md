---
title: Depuración de una aplicación JavaScript o TypeScript
description: Visual Studio proporciona compatibilidad para depurar aplicaciones de JavaScript y TypeScript en Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0405488f6f456f22711498e81789881ffc5a0a8a
ms.sourcegitcommit: 308a2bdbea81df78bffc3a01afce4ab13131fabc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913000"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Depuración de una aplicación JavaScript o TypeScript en Visual Studio

Puede depurar código JavaScript y TypeScript con Visual Studio. Puede establecer y alcanzar puntos de interrupción, asociar el depurador, inspeccionar variables, ver la pila de llamadas y usar otras características de depuración.

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalarlo de forma gratuita. Según la forma en que vaya a desarrollar la aplicación, es posible que tenga que instalar la **carga de trabajo de desarrollo Node.js** con Visual Studio.

## <a name="debug-server-side-script"></a>Depurar scripts del servidor

1. Con el proyecto abierto en Visual Studio, abra un archivo JavaScript del servidor (como *server.js*) y haga clic en el medianil hacia el medianil izquierdo para establecer un punto de interrupción:

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

1. Para ejecutar la aplicación, presione **F5** (**Depurar** > **Iniciar depuración**).

    El depurador se detiene en el punto de interrupción establecido (la instrucción actual está marcada en amarillo). Ahora, puede inspeccionar el estado de la aplicación desplazando el puntero sobre las variables que están actualmente en el ámbito, con ventanas del depurador como **Locales** e **Inspección**.

1. Presione **F5** para continuar la aplicación.

1. Si quiere utilizar las herramientas de desarrollo de Chrome o Herramientas de F12, presione **F12**. Puede usar estas herramientas para examinar el DOM e interactuar con la aplicación mediante la consola de JavaScript.

## <a name="debug-client-side-script"></a>Depurar scripts de cliente

::: moniker range=">=vs-2019"
Visual Studio proporciona compatibilidad con la depuración del lado cliente solo para Chrome y Microsoft Edge (Chromium). En algunos escenarios, el depurador alcanza automáticamente los puntos de interrupción en los códigos JavaScript y TypeScript y en scripts insertados en archivos HTML. Para depurar scripts del lado cliente en aplicaciones ASP.NET, vea la entrada de blog sobre [depuración de JavaScript en Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) y esta [publicación para Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio proporciona compatibilidad con la depuración del lado cliente solo para Internet Explorer y Chrome. En algunos escenarios, el depurador alcanza automáticamente los puntos de interrupción en los códigos JavaScript y TypeScript y en scripts insertados en archivos HTML. Para depurar scripts del lado cliente en aplicaciones ASP.NET, vea la entrada de blog sobre [depuración del lado cliente de proyectos de ASP.NET en Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Para aplicaciones que no sean ASP.NET, siga los pasos que se describen aquí.

### <a name="prepare-your-app-for-debugging"></a>Preparación de la aplicación para la depuración

Si el origen se han minimizado o creado mediante un transcompilador como TypeScript o Babel, será necesario recurrir a [asignaciones de origen](#generate_source_maps) para lograr la mejor experiencia de depuración. Sin los mapas de origen, el depurador se puede seguir asociando a un script de cliente en ejecución, pero solo podrá establecer y alcanzar puntos de interrupción en el archivo minimizado o transcompilado, no en el archivo de origen. Por ejemplo, en una aplicación Vue.js, el script minimizado se pasa como una cadena a una instrucción `eval`, y no hay ninguna manera de recorrer este código de forma efectiva con el depurador de Visual Studio, a menos que se usen mapas de origen. En escenarios de depuración complejos, en su lugar también se podrían usar las herramientas de desarrollo de Chrome o las Herramientas de F12 para Microsoft Edge.

Para obtener ayuda para generar mapas de origen, vea [Generación de mapas de origen para la depuración](#generate_source_maps).

### <a name="prepare_the_browser_for_debugging"></a> Preparación del explorador para la depuración

::: moniker range=">=vs-2019"
Para este escenario, use Microsoft Edge (Chromium), denominado actualmente **Microsoft Edge Beta** en el IDE, o bien Chrome.
::: moniker-end
::: moniker range="vs-2017"
Para este escenario, use Chrome.
::: moniker-end

1. Cierre todas las ventanas del explorador de destino.

   Otras instancias del explorador pueden impedir que el explorador se abra con la depuración habilitada. (Puede que las extensiones de explorador estén en ejecución e impidan el modo de depuración completa, por lo que es posible que tenga que abrir el Administrador de tareas para encontrar instancias inesperadas de Chrome).

   ::: moniker range=">=vs-2019"
   En el caso de Microsoft Edge (Chromium), cierre también todas las instancias de Chrome. Como los dos exploradores usan el código base de chromium, se obtiene el mejor resultado.
   ::: moniker-end

2. Inicie el explorador con la depuración habilitada.

    ::: moniker range=">=vs-2019"
    A partir de Visual Studio 2019, puede establecer la marca `--remote-debugging-port=9222` al iniciar el explorador si selecciona **Explorar con...** > en la barra de herramientas **Depurar**, elige **Agregar** y, después, establece la marca en el campo **Argumentos**. Use otro nombre descriptivo para el explorador, como **Edge con depuración** o **Chrome con depuración**. Para obtener información detallada, vea las [notas de la versión](/visualstudio/releases/2019/release-notes-v16.2).

    ![Establezca el explorador para que se abra con la depuración habilitada.](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Como alternativa, abra el comando **Ejecutar** desde el botón **Inicio** de Windows (haga clic con el botón derecho y elija **Ejecutar**), y escriba el comando siguiente:

    `msedge --remote-debugging-port=9222`

    o bien,

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Abra el comando **Ejecutar** desde el botón **Inicio** de Windows (haga clic con el botón derecho y elija **Ejecutar**) y escriba el comando siguiente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Esto inicia el explorador con la depuración habilitada.

    La aplicación todavía no está en ejecución, por lo que se obtiene una página del explorador vacía.

### <a name="attach-the-debugger-to-client-side-script"></a>Asociación del depurador al script del lado cliente

Para asociar el depurador de Visual Studio y establecer puntos de interrupción en el código del lado cliente, el depurador necesita ayuda para identificar el proceso correcto. Esta es una manera de habilitar esta opción.

1. Cambie a Visual Studio y, después, establezca un punto de interrupción en el código fuente, que puede ser un archivo de JavaScript, TypeScript o JSX. (Establezca el punto de interrupción en una línea de código que los permita, como una instrucción return o una declaración var).

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Para buscar el código específico en un archivo transpilado, presione **Ctrl**+**F** (**Editar** > **Buscar y reemplazar** > **Búsqueda rápida**).

    En el código del lado cliente, para alcanzar un punto de interrupción en un archivo de TypeScript o JSX, normalmente es necesario usar [mapas de origen](#generate_source_maps). Un mapa de origen debe estar configurado correctamente para admitir la depuración en Visual Studio.

2. Seleccione el explorador de destino como destino de depuración en Visual Studio y después presione **Ctrl**+**F5** (**Depurar** > **Iniciar sin depurar**) para ejecutar la aplicación en el explorador.

    ::: moniker range=">=vs-2019"
    Si ha creado una configuración de explorador con un nombre descriptivo, elíjala como destino de depuración.
    ::: moniker-end

    La aplicación se abre en una nueva pestaña del explorador.

3. Elija **Depurar** > **Asociar al proceso**.

    > [!TIP]
    > A partir de Visual Studio 2017, una vez que se siguen estos pasos para asociar al proceso la primera vez, puede volver a asociar rápidamente al mismo proceso si selecciona **Depurar** > **Reasociar al proceso**.

4. En el cuadro de diálogo **Asociar al proceso**, obtendrá una lista filtrada de las instancias del explorador a las que se puede asociar.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, elija el depurador correcto para el explorador de destino, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** en el campo **Asociar a:** , escriba **chrome** o **edge** en el cuadro de filtro para filtrar los resultados de la búsqueda.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **Código WebKit** en el campo **Asociar a** y escriba **chrome** en el cuadro de filtro para filtrar los resultados de la búsqueda.
    ::: moniker-end

5. Seleccione el proceso de explorador con el puerto de host correcto (localhost en este ejemplo) y seleccione **Asociar**.

    Es posible que también aparezca el puerto (por ejemplo, 1337) en el campo **Título** para facilitar la selección de la instancia correcta del explorador.

    ::: moniker range=">=vs-2019"
    En el ejemplo siguiente se muestra qué aspecto tiene para el explorador Microsoft Edge (Chromium).

    ![Asociar al proceso](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Asociar al proceso](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Sabrá que el depurador se ha asociado correctamente cuando el Explorador DOM y la Consola de JavaScript se abran correctamente en Visual Studio. Estas herramientas de depuración son similares a las herramientas de desarrollo de Chrome y a Herramientas F12 para Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Si el depurador no se asocia y aparece el mensaje "No se pudo iniciar el adaptador de depuración" o "No se puede asociar al proceso. Existe una operación que no es legal en el estado actual.", use el Administrador de tareas de Windows para cerrar todas las instancias del explorador de destino antes de iniciarlo en modo de depuración. Es posible que las extensiones del explorador estén en ejecución y eviten el modo de depuración completa.

6. Como es posible que el código con el punto de interrupción ya se haya ejecutado, actualice la página del explorador. Si es necesario, realice una acción para que se ejecute el código con el punto de interrupción.

    Mientras está en pausa en el depurador, puede pasar el mouse sobre las variables y usar las ventanas del depurador para examinar el estado de la aplicación. Para avanzar el depurador, puede ejecutar el código paso a paso (**F5**, **F10** y **F11**). Para más información sobre las características de depuración básicas, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

    Puede alcanzar el punto de interrupción en el archivo *.js* transpilado o en el de código fuente, en función del tipo de aplicación, de los pasos que haya seguido antes y de otros factores como el estado del explorador. En cualquier caso, puede ejecutar paso a paso el código y examinar las variables.

   * Si tiene que interrumpir el código en un archivo de origen TypeScript, JSX o *.vue*, y no puede hacerlo, asegúrese de que el entorno esté configurado correctamente, como se describe en la sección [Solución de problemas](#troubleshooting_source_maps).

   * Si tiene que interrumpir el código en un archivo JavaScript transcompilado (por ejemplo, *app-bundle.js*) y no puede hacerlo, quite el archivo de mapa de origen, *nombreDeArchivo.js.map*.

### <a name="troubleshooting_source_maps"></a> Solución de problemas de puntos de interrupción y mapas de origen

Si tiene que interrumpir el código en un archivo de origen TypeScript o JSX y no puede hacerlo, use **Asociar al proceso**, como se describe en los pasos anteriores para asociar el depurador. Asegúrese de que el entorno está configurado correctamente:

* Ha cerrado todas las instancias del explorador, incluidas las extensiones de Chrome (mediante el Administrador de tareas), para que pueda ejecutar el explorador en modo de depuración.
      
* Asegúrese de [iniciar el explorador en modo de depuración](#prepare_the_browser_for_debugging).

* Asegúrese de que el archivo de mapa de origen incluye la ruta de acceso relativa correcta al archivo de código fuente y que no incluye prefijos no admitidos, como *webpack:///* , lo que impide que el depurador de Visual Studio busque un archivo de código fuente. Por ejemplo, una referencia como *webpack:///.app.tsx* se podría corregir como *./app.tsx*. Puede hacerlo manualmente en el archivo de mapa de origen (que es útil para las pruebas) o a través de una configuración de compilación personalizada. Para más información, vea [Generación de mapas de origen para la depuración](#generate_source_maps).

Como alternativa, si tiene que interrumpir el código en un archivo de código fuente (por ejemplo, *app.tsx*) y no puede hacerlo, intente usar la instrucción `debugger;` en el archivo de código fuente, o bien establezca puntos de interrupción en las herramientas de desarrollo de Chrome (o las Herramientas de F12 para Microsoft Edge).

## <a name="generate_source_maps"></a> Generar mapas de origen para la depuración

Visual Studio tiene la capacidad de usar y generar mapas de origen en archivos de código fuente de JavaScript. Esto suele ser necesario cuando el origen se ha minimizado o creado mediante un transcompilador como TypeScript o Babel. Las opciones disponibles dependen del tipo de proyecto.

* Un proyecto de TypeScript en Visual Studio genera mapas de origen de forma automática y predeterminada. Para más información, vea [Configuración de mapas de origen con un archivo tsconfig.json](#configure_source_maps).

* En un proyecto de JavaScript, puede generar mapas de origen mediante un software que instala varios programas como webpack y un compilador como TypeScript (o Babel), que puede agregar al proyecto. En el caso del compilador de TypeScript, también tendrá que agregar un archivo *tsconfig.json* y establecer la opción de compilador `sourceMap`. Para obtener un ejemplo que muestra cómo llevar esto a cabo mediante una configuración de webpack básica, vea [Creación de una aplicación Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Si no está familiarizado con los mapas de origen, lea [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Introducción a los mapas de origen de JavaScript) antes de continuar. 

Para configurar opciones avanzadas de mapas de origen, utilice un archivo *tsconfig.json* o la configuración del proyecto en un proyecto de TypeScript, pero no ambos.

Para habilitar la depuración con Visual Studio, debe asegurarse de que las referencias al archivo de código fuente en el mapa de origen generado son correctas (esto puede requerir pruebas). Por ejemplo, si usa webpack, las referencias del archivo de mapa de origen incluyen el prefijo *webpack:///* , lo que impide que Visual Studio busque un archivo de origen TypeScript o JSX. En concreto, cuando esto se corrige con fines de depuración, la referencia al archivo de código fuente (como *app.tsx*) se debe cambiar de algo como *webpack:///./app.tsx* a algo como *./app.tsx*, que permite la depuración (la ruta de acceso es relativa al archivo de código fuente). En el ejemplo siguiente se muestra cómo puede configurar los mapas de origen en webpack, que es uno de los productos de software que instala varios programas más comunes, para que funcionen con Visual Studio.

(Solo webpack) Si va a configurar el punto de interrupción en un archivo TypeScript o JSX (en lugar de un archivo de JavaScript transpilado), tendrá que actualizar la configuración de webpack. Por ejemplo, en *webpack-config.js*, es posible que deba reemplazar el código siguiente:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

con este código:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Se trata de una configuración solo de desarrollo para habilitar la depuración del código del lado cliente en Visual Studio.

En escenarios complicados, las herramientas del explorador (**F12**) a veces funcionan mejor para la depuración, ya que no requieren cambios en los prefijos personalizados.

### <a name="configure_source_maps"></a> Configuración de mapas de origen con un archivo tsconfig.json

Si agrega un archivo *tsconfig.json* al proyecto, Visual Studio trata la raíz del directorio como un proyecto de TypeScript. Para agregar el archivo, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y, luego, elija **Agregar > Nuevo elemento > Archivo de configuración JSON de TypeScript**. Un archivo *tsconfig.json* como este de aquí se agregará al proyecto.

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
* **mapRoot**: especifica la ubicación donde el depurador debe encontrar los archivos de mapa de origen ( *.map*) en lugar de la ubicación predeterminada. Use esta marca si los archivos *.map* en tiempo de ejecución deben estar en una ubicación diferente a la de los archivos *.js*. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación de los archivos *.map*.
* **sourceMap**: genera el archivo *.map* correspondiente.
* **sourceRoot**: especifica la ubicación en la que el depurador debe encontrar los archivos TypeScript en lugar de las ubicaciones de origen. Use esta marca si los orígenes en tiempo de ejecución deben estar en una ubicación diferente a la ubicación en tiempo de diseño. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de origen.

Para obtener más detalles sobre las opciones del compilador, eche un vistazo a la página [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html) (Opciones del compilador) en el manual de TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configuración de mapas de origen con la configuración del proyecto (proyecto de TypeScript)

La configuración de los mapas de origen también se puede establecer mediante las propiedades del proyecto, haciendo clic con el botón derecho en el proyecto y eligiendo **Proyecto > Propiedades > Compilación de TypeScript > Depuración**.

Encontrará disponibles estas opciones de proyecto.

* **Generar mapas de origen** (equivalente a **sourceMap** en *tsconfig.json*): genera el archivo *.map* correspondiente.
* **Especificar el directorio raíz de los mapas de origen** (equivalente a **mapRoot** en *tsconfig.json*): especifica la ubicación en la que el depurador debe encontrar los archivos de mapa en lugar de las ubicaciones generadas. Use esta marca si los archivos *.map* en tiempo de ejecución deben estar en una ubicación diferente a la de los archivos .js. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de mapa.
* **Especificar el directorio raíz de los archivos TypeScript** (equivalente a **sourceRoot** en *tsconfig.json*): especifica la ubicación en la que el depurador debe encontrar los archivos TypeScript en lugar de las ubicaciones de origen. Use esta marca si los archivos de origen en tiempo de ejecución deben estar en una ubicación diferente a la ubicación en tiempo de diseño. La ubicación especificada está insertada en el mapa de origen para dirigir al depurador a la ubicación donde están los archivos de origen.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Depurar JavaScript en archivos dinámicos con Razor (ASP.NET)

::: moniker range=">=vs-2019"
A partir de Visual Studio 2019, Visual Studio proporciona compatibilidad con la depuración solo para Chrome y Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio admite la depuración de Internet Explorer y Chrome únicamente.
::: moniker-end

Pero los puntos de interrupción no se pueden alcanzar de forma automática en los archivos generados con sintaxis de Razor (cshtml, vbhtml). Para depurar este tipo de archivos, se pueden utilizar dos métodos:

* **Colocar la instrucción `debugger;` donde quiera realizar la interrupción**: esto hace que el script dinámico detenga la ejecución e inicie la depuración inmediatamente mientras se está creando.
* **Cargar la página y abrir el documento dinámico en Visual Studio**: para que este método funcione, deberá abrir el archivo dinámico durante la depuración, establecer el punto de interrupción y actualizar la página. Dependiendo de si usa Chrome o Internet Explorer, encontrará el archivo mediante una de las estrategias siguientes:

   En Chrome, vaya a **Explorador de soluciones > Documentos de Script > nombreDeLaPágina**.

    > [!NOTE]
    > Al usar Chrome, podría obtener un mensaje de tipo **no hay código fuente disponible entre etiquetas \<script>** . Esto es normal, simplemente continúe con la depuración.

   ::: moniker range=">=vs-2019"
   En el caso de Microsoft Edge (Chromium), use el mismo procedimiento que en Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   En Internet Explorer, vaya a **Explorador de soluciones > Documentos de Script > Windows Internet Explorer > nombreDeLaPágina**.
   ::: moniker-end

Para más información, vea [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Depuración del lado cliente de proyectos de ASP.NET en Google Chrome).
