---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: gewarren
author: gewarren
manager: jillfra
ms.topic: include
ms.openlocfilehash: 2d0d46a39bed9600ccdc0a7f343accf74378b81e
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820884"
---
El *entorno de desarrollo integrado* de Visual Studio es un panel de inicio creativo que se puede usar para editar, depurar y compilar código y, después, publicar una aplicación. Un entorno de desarrollo integrado (IDE) es un programa con numerosas características que se pueden usar para muchos aspectos del desarrollo de software. Más allá del editor estándar y el depurador que proporcionan la mayoría de IDE, Visual Studio incluye compiladores, herramientas de finalización de código, diseñadores gráficos y muchas más características para facilitar el proceso de desarrollo de software.

::: moniker range="vs-2017"

![El IDE de Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![El IDE de Visual Studio de 2019](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

En esta imagen se muestra Visual Studio con un proyecto abierto y varias ventanas de herramientas clave que probablemente usará:

- El [Explorador de soluciones](../../ide/solutions-and-projects-in-visual-studio.md) (parte superior derecha) permite ver, navegar y administrar los archivos de código. El **Explorador de soluciones** puede ayudar a organizar el código al agrupar los archivos en [soluciones y proyectos](../tutorial-projects-solutions.md).

- La [ventana del editor](../../ide/writing-code-in-the-code-and-text-editor.md) (centro), donde es probable que pase la mayor parte del tiempo, muestra el contenido del archivo. Es donde puede editar código o diseñar una interfaz de usuario, como una ventana con botones y cuadros de texto.

::: moniker range="vs-2017"

- La ventana [Resultados](../../ide/reference/output-window.md) (parte inferior central) es donde Visual Studio envía notificaciones, como mensajes de error y de depuración, advertencias del compilador, mensajes de estado de publicación, etc. Cada código fuente de mensaje tiene su propia pestaña.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (parte inferior derecha) permite realizar el seguimiento de los elementos de trabajo y compartir código con otros usuarios mediante tecnologías de control de versiones como [Git](https://git-scm.com/) y [Control de versiones de Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Ediciones

::: moniker range="vs-2017"

Visual Studio está disponible para Windows y Mac. [Visual Studio para Mac](/visualstudio/mac/) tiene muchas de las mismas características que Visual Studio 2017 y está optimizado para el desarrollo de aplicaciones móviles y multiplataforma. Este artículo se centra en la versión de Windows de Visual Studio 2017.

Existen tres ediciones de Visual Studio 2017: Community, Professional y Enterprise. Vea [Comparar los IDE de Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) para obtener información sobre las características que se admiten en cada edición.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio está disponible para Windows y Mac. [Visual Studio para Mac](/visualstudio/mac/) tiene muchas de las mismas características que Visual Studio 2019 y está optimizado para el desarrollo de aplicaciones móviles y multiplataforma. Este artículo se centra en la versión de Windows de Visual Studio 2019.

Existen tres ediciones de Visual Studio 2019: Community, Professional y Enterprise. Consulte [Comparar los IDE de Visual Studio](https://visualstudio.microsoft.com/vs/compare/) para obtener información sobre las características que se admiten en cada edición.

::: moniker-end

## <a name="popular-productivity-features"></a>Características de productividad populares

Algunas de las características populares de Visual Studio que ayudan a ser más productivos durante el desarrollo de software incluyen:

- Subrayados ondulados y [Acciones rápidas](../../ide/quick-actions.md)

   Los subrayados ondulados son rayas con formas de onda debajo de las palabras que alertan de errores o posibles problemas en el código a medida que se escribe. Estas pistas visuales permiten corregir problemas inmediatamente sin esperar a que el error se detecte durante la compilación o cuando se ejecute el programa. Si mantiene el cursor sobre un subrayado ondulado, se ve información adicional sobre el error. También puede aparecer una bombilla en el margen izquierdo con acciones, conocidas como Acciones rápidas, para corregir el error.

   ![Subrayados ondulados en Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Limpieza de código

   Con solo un clic en un botón, puede dar formato al código y aplicar cualquier corrección de código sugerida por la [configuración del estilo del código](../../ide/reference/options-text-editor-csharp-formatting.md), las [convenciones de .editorconfig](../../ide/create-portable-custom-editor-options.md) y los [analizadores de Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Limpieza de código** ayuda a solucionar problemas con el código antes de la revisión del código. (Actualmente solo está disponible para el código de C#).

   ![Botón Limpieza de código de Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactorización](../../ide/refactoring-in-visual-studio.md)

   La refactorización incluye operaciones como el cambio de nombre inteligente de variables, la extracción de una o más líneas de código en un nuevo método, el cambio del orden de los parámetros de método, etc.

   ![Refactorización en Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense es un término que define un conjunto de características que muestran información sobre el código directamente en el editor y, en algunos casos, escriben pequeños fragmentos de código automáticamente. Es como tener documentación básica insertada en el editor, lo que evita tener que buscar información escrita en cualquier otro lugar. Las características de IntelliSense varían según el lenguaje. Para más información, vea [IntelliSense para C#](../../ide/visual-csharp-intellisense.md), [IntelliSense para Visual C++](../../ide/visual-cpp-intellisense.md), [IntelliSense para JavaScript](../../ide/javascript-intellisense.md) e [IntelliSense de Visual Basic](../../ide/visual-basic-specific-intellisense.md). La siguiente ilustración muestra cómo IntelliSense muestra una lista de miembros de un tipo:

   ![Lista de miembros de Visual Studio](../media/intellisense-list-members.png)

- Cuadro de búsqueda

   Visual Studio puede parecer abrumador a veces con tantas propiedades, opciones y menús. El cuadro de búsqueda supone una excelente manera de encontrar rápidamente lo que necesita en Visual Studio. Al empezar a escribir el nombre de lo que está buscando, Visual Studio muestra resultados que llevan exactamente a donde necesita ir. Si necesita agregar funcionalidad a Visual Studio para, por ejemplo, agregar compatibilidad con otro lenguaje de programación, el cuadro de búsqueda proporciona resultados que abren el Instalador de Visual Studio para instalar un componente individual o una carga de trabajo.

   > [!TIP]
   > Presione **Ctrl**+**Q** como acceso directo al cuadro de búsqueda.

   ::: moniker range="vs-2017"

   ![Cuadro de búsqueda Inicio rápido de Visual Studio 2017](../media/quick-launch-nuget.png)

   Para más información, vea [Inicio rápido](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Cuadro de búsqueda de Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Edite y depure colaborativamente con otros usuarios en tiempo real, sin importar el tipo de aplicación o el lenguaje de programación. Puede compartir al instante y de manera segura su proyecto y, según sea necesario, las sesiones de depuración, las instancias de terminal, las aplicaciones web de localhost, las llamadas de voz, etc.

- [Jerarquía de llamadas](../../ide/reference/call-hierarchy.md)

   En la ventana **Jerarquía de llamadas** se muestran los métodos que llaman a un método seleccionado. Puede ser información útil si está pensando en cambiar o quitar el método, o si está intentando realizar un seguimiento de un error.

   ![Ventana Jerarquía de llamadas](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens ayuda a buscar referencias al código, cambios en él, errores vinculados, elementos de trabajo, revisiones de código y pruebas unitarias, todo sin salir del editor.

   ![CodeLens](../media/codelens-overview.png)

- [Ir a definición](../../ide/go-to-and-peek-definition.md)

   La característica Ir a definición lleva directamente a la ubicación donde se define una función o un tipo.

   ![Ir a definición](../media/go-to-definition-menu.png)

- [Ver la definición](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   En la ventana **Ojear la definición** se muestra la definición de un tipo o método sin abrir en realidad un archivo independiente.

   ![Ojear la definición](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalación del IDE de Visual Studio

En esta sección, creará un proyecto sencillo para probar algo de lo que puede hacer con Visual Studio. Usará [IntelliSense](../../ide/using-intellisense.md) como ayuda para codificar, depurará una aplicación para ver el valor de una variable durante la ejecución del programa y cambiará el tema de color.

::: moniker range="vs-2017"

Para empezar, [descargue Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e instálelo en su sistema. El instalador modular le permite elegir e instalar *cargas de trabajo*, que son grupos de características necesarias para el lenguaje de programación o la plataforma que prefiera. Siga los pasos para [crear un programa](#create-a-program) y no se olvide de seleccionar la carga de trabajo **Desarrollo multiplataforma de .NET Core** durante la instalación.

::: moniker-end

::: moniker range=">=vs-2019"

Para empezar, [descargue Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) e instálelo en su sistema. El instalador modular le permite elegir e instalar *cargas de trabajo*, que son grupos de características necesarias para el lenguaje de programación o la plataforma que prefiera. Siga los pasos para [crear un programa](#create-a-program) y no se olvide de seleccionar la carga de trabajo **Desarrollo multiplataforma de .NET Core** durante la instalación.

::: moniker-end

![Carga de trabajo de desarrollo multiplataforma de .NET Core en el Instalador de Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Cuando se abre Visual Studio por primera vez, se puede [iniciar sesión](../../ide/signing-in-to-visual-studio.md) opcionalmente con la cuenta de Microsoft o con la cuenta profesional o educativa.

## <a name="create-a-program"></a>Creación de un programa

Vamos a profundizar y crear un programa sencillo.

::: moniker range="vs-2017"

1. Abra Visual Studio.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

   ![Archivo > Nuevo proyecto en la barra de menús](../media/file-new-project-menu.png)

   En el cuadro de diálogo **Nuevo proyecto** se muestran varias *plantillas* de proyecto. Una plantilla contiene los archivos básicos y la configuración necesaria para un tipo de proyecto concreto.

1. Elija la categoría de plantilla **.NET Core** bajo **Visual C#** y, después, elija la plantilla **Aplicación de consola (.NET Core)** . En el cuadro de texto **Nombre**, escriba **HelloWorld** y después haga clic en el botón **Aceptar**.

   ![Plantilla de aplicación de .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Si no ve la categoría **.NET Core**, debe instalar la carga de trabajo de **Desarrollo multiplaforma de .NET Core**. Para ello, elija el vínculo **Abrir el instalador de Visual Studio** en el panel inferior izquierdo del cuadro de diálogo **Nuevo proyecto**. Una vez que se abra el Instalador de Visual Studio, desplácese hacia abajo y seleccione la carga de trabajo de **desarrollo multiplataforma de .NET Core** y luego **Modificar**.

   Visual Studio crea el proyecto. Es una aplicación "Hola mundo" sencilla que llama al método <xref:System.Console.WriteLine?displayProperty=nameWithType> para mostrar la cadena literal "¡Hola mundo!" en la ventana de la consola (salida del programa).

   En breve, debería ver algo parecido a lo siguiente:

   ![IDE de Visual Studio](../media/overview-ide-console-app.png)

   En la ventana del editor se muestra el código de C# de la aplicación, que ocupa la mayor parte del espacio. Observe que el texto se colorea automáticamente para indicar diferentes partes del código, como palabras clave y tipos. Además, líneas pequeñas, verticales y discontinuas en el código indican qué llaves coinciden, y los números de línea sirven para ubicar código más adelante. Puede elegir el pequeño signo menos de la casilla para contraer o expandir bloques de código. Esta característica de esquematización de código le permite ocultar el código que no necesita, ayudando a minimizar el desorden en la pantalla. Los archivos del proyecto se muestran en el lado derecho de una ventana llamada **Explorador de soluciones**.

   ![IDE de Visual Studio con cuadros rojos](../media/overview-ide-console-app-red-boxes.png)

   Hay otros menús y ventanas de herramientas disponibles, pero por ahora vamos a continuar.

1. Ahora, inicie la aplicación. Para ello, elija **Iniciar sin depurar** en el menú **Depurar** de la barra de menús. También puede presionar **Ctrl**+**F5**.

   ![Menú Depurar > Iniciar sin depurar](../media/overview-start-without-debugging.png)

   Visual Studio compila la aplicación y se abre una ventana de consola con el mensaje **¡Hola mundo!** ¡Ya tiene una aplicación en ejecución!

   ![Ventana de consola](../media/overview-console-window.png)

1. Para cerrar la ventana de consola, presione cualquier tecla del teclado.

1. Ahora vamos a agregar código adicional a la aplicación. Agregue el siguiente código de C# antes de la línea que dice `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Este código muestra **What is your name?** en la ventana de la consola y espera a que el usuario escriba algún texto seguido de la tecla **Entrar**.

1. Cambie la línea que indica `Console.WriteLine("Hello World!");` por el código siguiente:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Vuelva a ejecutar la aplicación mediante la selección de **Depurar** > **Iniciar sin depurar** o presionando **Ctrl**+**F5**.

   Visual Studio recompila la aplicación y se abre una ventana de consola que le solicita su nombre.

1. Escriba su nombre en la ventana de consola y presione **Entrar**.

   ![Entrada de la ventana de consola](../media/overview-console-input.png)

1. Presione cualquier tecla para cerrar la ventana de consola y detener la ejecución del programa.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

   La ventana de inicio aparece con varias opciones para clonar un repositorio, abrir un proyecto reciente o crear un proyecto.

1. Elija **Crear un nuevo proyecto**.

   ![Opción Crear un proyecto en la ventana de inicio de Visual Studio](../media/vs-2019/start-window-create-new-project.png)

   La ventana **Crear un nuevo proyecto** se abre y muestra varias *plantillas* de proyecto. Una plantilla contiene los archivos básicos y la configuración necesaria para un tipo de proyecto concreto.

1. Para buscar la plantilla que quiere, escriba **consola .net core** en el cuadro de búsqueda. La lista de plantillas disponibles se filtra automáticamente en función de las palabras clave que escribió. Para filtrar aún más los resultados de las plantillas, elija **C#** en la lista desplegable **Lenguaje**. Seleccione la plantilla **Aplicación de consola (.NET Core)** y haga clic en **Siguiente**.

    ![Creación de un proyecto nuevo en Visual Studio](../media/vs-2019/create-new-project.png)

1. En la ventana **Configure su nuevo proyecto**, escriba **HelloWorld** en el cuadro **Nombre del proyecto** y, si quiere, cambie la ubicación del directorio de los archivos del proyecto y, a continuación, elija **Crear**.

   ![Configuración de un nuevo proyecto en Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio crea el proyecto. Es una aplicación "Hola mundo" sencilla que llama al método <xref:System.Console.WriteLine?displayProperty=nameWithType> para mostrar la cadena literal "¡Hola mundo!" en la ventana de la consola (salida del programa).

   En breve, debería ver algo parecido a lo siguiente:

   ![IDE de Visual Studio](../media/vs-2019/overview-ide-console-app.png)

   En la ventana del editor se muestra el código de C# de la aplicación, que ocupa la mayor parte del espacio. Observe que el texto se colorea automáticamente para indicar diferentes partes del código, como palabras clave y tipos. Además, líneas pequeñas, verticales y discontinuas en el código indican qué llaves coinciden, y los números de línea sirven para ubicar código más adelante. Puede elegir el pequeño signo menos de la casilla para contraer o expandir bloques de código. Esta característica de esquematización de código le permite ocultar el código que no necesita, ayudando a minimizar el desorden en la pantalla. Los archivos del proyecto se muestran en el lado derecho de una ventana llamada **Explorador de soluciones**.

   ![IDE de Visual Studio con cuadros rojos](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Hay otros menús y ventanas de herramientas disponibles, pero por ahora vamos a continuar.

1. Ahora, inicie la aplicación. Para ello, elija **Iniciar sin depurar** en el menú **Depurar** de la barra de menús. También puede presionar **Ctrl**+**F5**.

   ![Menú Depurar > Iniciar sin depurar](../media/overview-start-without-debugging.png)

   Visual Studio compila la aplicación y se abre una ventana de consola con el mensaje **¡Hola mundo!** ¡Ya tiene una aplicación en ejecución!

   ![Ventana de consola](../media/vs-2019/overview-console-window.png)

1. Para cerrar la ventana de consola, presione cualquier tecla del teclado.

1. Ahora vamos a agregar código adicional a la aplicación. Agregue el siguiente código de C# antes de la línea que dice `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Este código muestra **What is your name?** en la ventana de la consola y espera a que el usuario escriba algún texto seguido de la tecla **Entrar**.

1. Cambie la línea que indica `Console.WriteLine("Hello World!");` por el código siguiente:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Vuelva a ejecutar la aplicación mediante la selección de **Depurar** > **Iniciar sin depurar** o presionando **Ctrl**+**F5**.

   Visual Studio recompila la aplicación y se abre una ventana de consola que le solicita su nombre.

1. Escriba su nombre en la ventana de consola y presione **Entrar**.

   ![Ventana de consola](../media/vs-2019/overview-console-input.png)

1. Presione cualquier tecla para cerrar la ventana de consola y detener la ejecución del programa.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Usar IntelliSense y la refactorización

Veamos un par de formas en las que la [refactorización](../../ide/refactoring-in-visual-studio.md) e [IntelliSense](../../ide/using-intellisense.md) pueden ayudar a crear código de forma más eficaz.

En primer lugar, vamos a cambiar el nombre de la variable `name`:

1. Haga doble clic en la variable `name` para seleccionarla.

2. Escriba el nombre nuevo de la variable, **username**.

   Observe que aparece un cuadro gris alrededor de la variable y una bombilla en el margen.

::: moniker range="vs-2017"

3. Haga clic en el icono de bombilla para mostrar las [Acciones rápidas](../../ide/quick-actions.md) disponibles. Seleccione **Rename 'name' to 'username'** (Cambiar "name" a "username").

   ![Acción de cambio de nombre en Visual Studio](../media/rename-quick-action.png)

   Se cambia el nombre de la variable en el proyecto, que en nuestro caso es solo en dos lugares.

   ![Gif animado en el que se muestra la operación de refactorización de cambio de nombre en Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Haga clic en el icono de bombilla para mostrar las [Acciones rápidas](../../ide/quick-actions.md) disponibles. Seleccione **Rename 'name' to 'username'** (Cambiar "name" a "username").

   ![Acción de cambio de nombre en Visual Studio](../media/vs-2019/rename-quick-action.png)

   Se cambia el nombre de la variable en el proyecto, que en nuestro caso es solo en dos lugares.

::: moniker-end

4. Ahora echemos un vistazo a IntelliSense. Por debajo de la línea que dice `Console.WriteLine($"\nHello {username}!");`, escriba `DateTime now = DateTime.`.

   Los miembros de la clase <xref:System.DateTime> se muestran en un cuadro. Además, la descripción del miembro seleccionado actualmente se muestra en un cuadro independiente.

   ![IntelliSense enumera los miembros en Visual Studio](../media/intellisense-list-members.png)

5. Seleccione el miembro denominado **Now**, que es una propiedad de la clase, haciendo doble clic en él o presionando la tecla **Tab**. Agregue un punto y coma al final de la línea de código para completarla.

6. Por debajo, escriba o pegue las líneas de código siguientes:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> es algo diferente a <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ya que no añade un terminador de línea después de la impresión. Esto significa que el siguiente fragmento de texto que se envía a la salida se imprimirá en la misma línea. Puede mantener el ratón sobre cada uno de estos métodos en el código para ver su descripción.

7. A continuación, vamos a volver a usar la refactorización para que hacer que el código sea más conciso. Haga clic en la variable `now` en la línea `DateTime now = DateTime.Now;`.

   Observe que aparece un pequeño icono de destornillador en el margen de esa línea.

8. Haga clic en el icono de destornillador para ver las sugerencias disponibles en Visual Studio. En este caso, se muestra la refactorización [Variable temporal en línea](../../ide/reference/inline-temporary-variable.md) para quitar una línea de código sin cambiar el comportamiento general del código:

   ![Refactorización de variable temporal en línea en Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Haga clic en **Variable temporal en línea** para refactorizar el código.

::: moniker range="vs-2017"

10. Vuelva a ejecutar el programa presionando **Ctrl**+**F5**. La salida tendrá un aspecto similar a este:

    ![Ventana de consola con la salida del programa](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Vuelva a ejecutar el programa presionando **Ctrl**+**F5**. La salida tendrá un aspecto similar a este:

    ![Ventana de consola con la salida del programa](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Depurar código

Cuando se escribe código, debe ejecutarlo y probarlo para ver si hay errores. El sistema de depuración de Visual Studio permite examinar el código por cada instrucción e inspeccionar las variables a medida que se avanza. Puede establecer *puntos de interrupción* que detengan la ejecución del código en una línea determinada. Puede observar cómo cambia el valor de una variable a medida que el código se ejecuta, etc.

Vamos a establecer un punto de interrupción para ver el valor de la variable `username` mientras el programa se encuentra "en marcha".

1. Busque la línea de código en la que se indica `Console.WriteLine($"\nHello {username}!");`. Para establecer un punto de interrupción en esta línea de código, es decir, para que el programa detenga la ejecución en esta línea, haga clic en el margen izquierdo del editor. También puede hacer clic en cualquier lugar de la línea de código y, después, presionar **F9**.

   Aparece un círculo de color rojo en el margen izquierdo y el código se resalta en color rojo.

   ![Punto de interrupción en una línea de código en Visual Studio](../media/breakpoint.png)

1. Para iniciar la depuración, seleccione **Depurar** > **Iniciar depuración** o presione **F5**.

1. Cuando aparezca la ventana de consola y se le solicite su nombre, escríbalo y presione **Entrar**.

   El foco se devuelve al editor de código de Visual Studio y la línea de código con el punto de interrupción se resalta en color amarillo. Esto significa que es la siguiente línea de código que el programa va a ejecutar.

1. Mantenga el ratón sobre la variable `username` para ver su valor. Como alternativa, puede hacer clic con el botón derecho en `username` y seleccionar **Agregar inspección** para agregar la variable a la ventana **Inspección**, donde también puede ver su valor.

   ![Valor de la variable durante la depuración en Visual Studio](../media/debugging-variable-value.png)

1. Para permitir que el programa se ejecute hasta completarse, vuelva a presionar **F5**.

Para obtener más detalles sobre el proceso de depuración de Visual Studio, consulte [Paseo por las características del depurador](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Personalizar Visual Studio

Puede personalizar la interfaz de usuario de Visual Studio, incluso cambiar el tema de color predeterminado. Para cambiar al tema **Oscuro**:

1. En la barra de menús, seleccione **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**.

::: moniker range="vs-2017"

2. En la página de opciones **Entorno** > **General**, cambie la selección de **Tema de color** a **Oscuro** y, después, elija **Aceptar**.

   El tema de color para todo el IDE se cambia a **Oscuro**.

   ![Visual Studio con tema oscuro](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. En la página de opciones **Entorno** > **General**, cambie la selección de **Tema de color** a **Oscuro** y, después, elija **Aceptar**.

   El tema de color para todo el IDE se cambia a **Oscuro**.

   ![Visual Studio con tema oscuro](../media/vs-2019/dark-theme.png)

::: moniker-end

Para obtener información sobre otras maneras de personalizar el IDE, vea [Personalizar Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).