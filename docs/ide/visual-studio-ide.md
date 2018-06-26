---
title: Información general sobre Visual Studio 2017
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7667cac2a26a3e98d2e92dfeb13cee36d870e9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691165"
---
# <a name="visual-studio-ide-overview"></a>Introducción al IDE de Visual Studio

El entorno de desarrollo integrado (IDE) de Visual Studio es un panel de inicio creativo que se puede usar para ver y editar código y, después, depurar, compilar y publicar una aplicación.

Visual Studio está disponible para Windows y Mac. [Visual Studio para Mac](/visualstudio/mac/) tiene muchas de las mismas características que Visual Studio 2017 y está optimizado para el desarrollo de aplicaciones móviles y multiplataforma.

Este artículo se centra en Visual Studio 2017 para Windows. Presenta las características básicas del IDE. Se describirán algunas cosas que se pueden hacer con Visual Studio, incluida la creación de un proyecto simple, el uso de IntelliSense como ayuda para la codificación y la depuración de una aplicación para ver el valor de una variable durante la ejecución del programa. También se realizará un recorrido de las distintas ventanas de herramientas.

## <a name="install-the-visual-studio-ide"></a>Instalación del IDE de Visual Studio

Para comenzar, [descargue Visual Studio 2017](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) e instálelo en el sistema.

El instalador modular le permite elegir e instalar *cargas de trabajo*, que son grupos de características necesarias para el lenguaje de programación o la plataforma que prefiera. Siga los pasos para [crear un programa](#create-a-program) y no se olvide de seleccionar la carga de trabajo **Desarrollo multiplataforma de .NET Core** durante la instalación. En los temas de inicio rápido, como [Introducción a C++ en Visual Studio](getting-started-with-cpp-in-visual-studio.md), se incluyen instrucciones para la instalación de otras cargas de trabajo.

![Instalador de Visual Studio](../ide/media/overview-net-core-workload.png)

Cuando se inicia Visual Studio por primera vez, puede iniciar sesión opcionalmente con su cuenta Microsoft o con su cuenta profesional o educativa.

## <a name="tour-of-the-ide"></a>Paseo por el IDE

Para ofrecerle una amplia información gráfica de Visual Studio, la siguiente imagen muestra Visual Studio con un proyecto abierto junto con varias ventanas de herramientas clave que probablemente usará:

![El IDE de Visual Studio](../ide/media/visualstudioide.png)

- El [Explorador de soluciones](../ide/solutions-and-projects-in-visual-studio.md) le permite ver y navegar por sus archivos de código, así como administrarlos. El Explorador de soluciones puede ayudar a organizar el código agrupando los archivos en soluciones y proyectos.

- La ventana [Editor](../ide/writing-code-in-the-code-and-text-editor.md), que es donde probablemente pase más tiempo, muestra el código y le permite editar código fuente y diseñar una interfaz de usuario.

- La ventana [Salida](../ide/reference/output-window.md) es el lugar al que Visual Studio envía sus notificaciones, como mensajes de error y de depuración, advertencias del compilador, mensajes de estado de publicación y mucho más. Cada código fuente de mensaje tiene su propia pestaña.

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) permite realizar el seguimiento de elementos de trabajo y compartir código con otros usuarios mediante tecnologías de control de versiones como [Git](https://git-scm.com/) y [Control de versiones de Team Foundation (TFVC)](/vsts/tfvc/overview).

Aquí se muestran otras características de productividad populares en Visual Studio:

- [Refactorización](../ide/refactoring-in-visual-studio.md) incluye operaciones tales como el cambio inteligente de nombre de las variables, mover líneas seleccionadas de código a una función diferente, mover código a otras ubicaciones, reordenar los parámetros de una función y mucho más.

   ![Refactorización](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) es un término que aglutina un conjunto de características muy populares que muestran información escritura sobre el código directamente en el editor y, en algunos casos, escriben pequeños fragmentos de código automáticamente. Básicamente, IntelliSense es como tener documentación básica insertada en el editor, lo que evita tener que buscar información de escritura en una ventana de ayuda independiente. Las características de IntelliSense varían según el lenguaje. Para más información, vea [IntelliSense para C#](../ide/visual-csharp-intellisense.md), [IntelliSense para Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense para JavaScript](../ide/javascript-intellisense.md) e [IntelliSense de Visual Basic](../ide/visual-basic-specific-intellisense.md). La ilustración siguiente muestra algunas características de IntelliSense en funcionamiento:

   ![Lista de miembros de Visual Studio](../ide/media/vs2017_Intellisense.png)

- El cuadro de búsqueda [Inicio rápido](../ide/reference/quick-launch-environment-options-dialog-box.md) supone una excelente manera de encontrar rápidamente lo que necesita en Visual Studio. Simplemente empiece a escribir el nombre de lo que esté buscando y Visual Studio le mostrará resultados que le llevarán exactamente a donde quiere ir. En el **inicio rápido** también se muestran vínculos que inician el **Instalador de Visual Studio** para cualquier componente individual o carga de trabajo.

   ![Cuadro de búsqueda de inicio rápido](../ide/media/VSIDE_Tour_QuickLaunch.png)

- Los **subrayados ondulados** son rayas con formas de onda debajo de las palabras que alertan de errores o posibles problemas en el código en tiempo real a medida que escribe. Gracias a esta característica es posible corregir tales problemas de inmediato sin esperar a que el error se detecte durante la compilación o el tiempo de ejecución. Si mantiene el mouse sobre la línea ondulada, verá información adicional sobre el error. También puede aparecer una bombilla en el margen izquierdo con acciones para corregir el error. Para más información, consulte [Acciones rápidas](../ide/quick-actions.md).

   ![Subrayados ondulados](../ide/media/vs2017_squiggle.png)

- En el menú contextual del editor de texto, puede abrir la ventana [Jerarquía de llamadas](../ide/reference/call-hierarchy.md) para mostrar los métodos que llaman al método, y que son llamados por este, situado debajo del símbolo de intercalación (punto de inserción).

   ![Ventana Jerarquía de llamadas](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) le permite buscar referencias y cambios en el código, errores vinculados, elementos de trabajo, revisiones de código y pruebas unitarias, todo sin salir del editor.

   ![CodeLens](../ide/media/codelensoverview.png)

- La ventana [Ojear la definición](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) muestra un método o definición de tipo en línea, sin salir del contexto actual.

   ![Ojear la definición](../ide/media/VSIDE_peek_definition.png)

- La opción de menú contextual [Ir a definición](../ide/go-to-and-peek-definition.md) le lleva directamente al lugar donde se definen la función o el objeto. También hay otros comandos de navegación disponibles haciendo clic con el botón secundario en el editor.

   ![Ir a definición](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>Creación de un programa

Vamos a profundizar y crear un nuevo y sencillo programa.

1. Abra Visual Studio. En el menú, elija **Archivo** > **Nuevo** > **Proyecto**.

  ![Archivo > Nuevo proyecto en la barra de menús](../ide/media/VSIDE_Tour_NewProject1.png)

1. En el cuadro de diálogo **Nuevo proyecto** se muestran varias *plantillas* de proyecto. Una plantilla contiene los archivos básicos y la configuración necesaria para un tipo de proyecto concreto. Elija la categoría **.NET Core** bajo **Visual C#** y, después, elija la plantilla **Aplicación de consola (.NET Core)**. En el cuadro de texto **Nombre**, escriba **HelloWorld** y después haga clic en el botón **Aceptar**.

  ![Plantilla de aplicación de .NET Core](../ide/media/overview-new-project-dialog.png)

   Visual Studio crea el proyecto. Es una aplicación "Hola mundo" sencilla que llama al método <xref:System.Console.WriteLine?displayProperty=nameWithType> para mostrar la cadena literal "¡Hola mundo!" en la ventana de la consola.

  > [!NOTE]
  > Si no ve la categoría **.NET Core**, debe instalar la carga de trabajo de **Desarrollo multiplaforma de .NET Core**. Para ello, elija el vínculo **Abrir el instalador de Visual Studio** en el panel inferior izquierdo del cuadro de diálogo **Nuevo proyecto**. Una vez que se abra el **Instalador de Visual Studio**, desplácese hacia abajo y seleccione la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, haga clic en **Modificar**.

   En breve, debería ver algo parecido a lo siguiente:

   ![IDE de Visual Studio](../ide/media/overview-ide-console-app.png)

   En la ventana del editor se muestra el código de C# para la aplicación, que ocupa la mayor parte del espacio. Observe que el texto se colorea automáticamente para indicar diferentes aspectos del código, como palabras claves y tipos. Además, líneas pequeñas, verticales y discontinuas en el código indican qué llaves coinciden, y los números de línea sirven para ubicar código más adelante. Puede elegir el pequeño signo de menos en la casilla para contraer o expandir código. Esta característica de esquematización de código le permite ocultar el código que no necesita, ayudando a minimizar el desorden en la pantalla.

   Los archivos del proyecto se muestran en el lado derecho de una ventana llamada **Explorador de soluciones**.

  ![IDE de Visual Studio con cuadros rojos](../ide/media/overview-ide-console-app-red-boxes.png)

  Hay otros menús y ventanas de herramientas disponibles, pero por ahora vamos a continuar.

1. Ahora, inicie la aplicación. Para ello, elija **Iniciar sin depurar** en el menú **Depurar** de la barra de menús. También puede presionar **Ctrl**+**F5**.

  ![Menú Depurar > Iniciar sin depurar](../ide/media/overview-start-without-debugging.png)

  Visual Studio compila la aplicación y se abre una ventana de consola con el mensaje **¡Hola mundo!** ¡Ya tiene una aplicación en ejecución!

  ![Ventana de consola](../ide/media/overview-console-window.png)

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

   ![Entrada de la ventana de consola](media/overview-console-input.png)

1. Presione cualquier tecla para cerrar la ventana de consola y detener la ejecución del programa.

## <a name="use-refactoring-and-intellisense"></a>Usar IntelliSense y la refactorización

Veamos un par de formas en las que la [refactorización](refactoring-in-visual-studio.md) e [IntelliSense](using-intellisense.md) pueden ayudar a crear código de forma más eficaz.

En primer lugar, vamos a cambiar el nombre de la variable `name`:

1. Haga doble clic en la variable `name` para seleccionarla.

1. Escriba el nombre nuevo para la variable, `username`.

   Observe que aparece un cuadro gris alrededor de la variable y una bombilla en el margen.

1. Haga clic en el icono de bombilla para mostrar las [Acciones rápidas](quick-actions.md) disponibles. Seleccione **Rename 'name' to 'username'** (Cambiar "name" a "username").

   ![Acción de cambio de nombre en Visual Studio](media/rename-quick-action.png)

   Se cambia el nombre de la variable en el proyecto, que en nuestro caso es solo en dos lugares.

   ![Gif animado en el que se muestra la operación de refactorización de cambio de nombre en Visual Studio](media/rename-refactoring.gif)

1. Ahora echemos un vistazo a IntelliSense. Debajo de la línea que dice `Console.WriteLine($"\nHello {username}!");`, escriba **DateTime now = DateTime.**.

   Los miembros de la clase <xref:System.DateTime> se muestran en un cuadro. Además, la descripción del miembro seleccionado actualmente se muestra en un cuadro independiente.

   ![IntelliSense enumera los miembros en Visual Studio](media/intellisense-list-members.png)

1. Seleccione el miembro denominado **Now**, que es una propiedad de la clase, haciendo doble clic en él o presionando la tecla **Tab**. Complete la línea de código mediante la adición de un punto y coma **;**.

1. Por debajo, escriba o copie las líneas de código siguientes:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> es algo diferente a <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ya que no añade un terminador de línea después de la impresión. Esto significa que el siguiente fragmento de texto que se envía a la salida se imprimirá en la misma línea. Puede mantener el ratón sobre cada uno de estos métodos en el código para ver su descripción.

1. A continuación, vamos a volver a usar la refactorización para que hacer que el código sea más conciso. Haga clic en la variable `now` en la línea `DateTime now = DateTime.Now;`.

   Observe que aparece un pequeño icono de destornillador en el margen de esa línea.

1. Haga clic en el icono de destornillador para ver las sugerencias disponibles en Visual Studio. En este caso, se muestra la refactorización [Variable temporal en línea](reference/inline-temporary-variable.md) para quitar una línea de código sin cambiar el comportamiento general:

   ![Refactorización de variable temporal en línea en Visual Studio](media/inline-temporary-variable-refactoring.png)

1. Haga clic en **Variable temporal en línea** para refactorizar el código.

1. Vuelva a ejecutar el programa presionando **Ctrl**+**F5**. La salida tendrá un aspecto similar a este:

   ![Ventana de consola con la salida del programa](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>Depurar código

Cuando se escribe código, debe ejecutarlo y probarlo para ver si hay errores. El sistema de depuración de Visual Studio permite examinar el código por cada instrucción e inspeccionar las variables a medida que se avanza. Puede establecer puntos de interrupción que solo se alcanzan cuando una condición especificada es verdadera. Puede supervisar los valores de las variables a medida que se ejecuta el código, entre otras cosas.

Vamos a establecer un punto de interrupción para ver el valor de la variable `username` mientras el programa se encuentra "en marcha".

1. Busque la línea de código en la que se indica `Console.WriteLine($"\nHello {username}!");`. Para establecer un punto de interrupción en esta línea de código, es decir, para que el programa detenga la ejecución en esta línea, haga clic en el margen izquierdo del editor. También puede hacer clic en cualquier lugar de la línea de código y, después, presionar **F9**.

   Aparece un círculo de color rojo en el margen izquierdo y el código se resalta en color rojo.

   ![Punto de interrupción en una línea de código en Visual Studio](media/breakpoint.png)

1. Para iniciar la depuración, seleccione **Depurar** > **Iniciar depuración** o presione **F5**.

1. Cuando aparezca la ventana de consola y se le solicite su nombre, escríbalo y presione **Entrar**.

   Observe que el foco se devuelve al editor de código de Visual Studio y la línea de código con el punto de interrupción se resalta en color amarillo. Esto significa que es la siguiente línea de código que el programa va a ejecutar.

1. Mantenga el ratón sobre la variable `username` para ver su valor. Como alternativa, puede hacer clic con el botón derecho en `username` y seleccionar **Agregar inspección** para agregar la variable a la ventana **Inspección**, donde también puede ver su valor.

   ![Valor de la variable durante la depuración en Visual Studio](media/debugging-variable-value.png)

1. Para permitir que el programa se ejecute hasta completarse, vuelva a presionar **F5**.

Para obtener más detalles sobre el proceso de depuración de Visual Studio, consulte [Paseo por las características del depurador](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Personalizar Visual Studio

Puede personalizar el IDE, incluido el tema de color predeterminado. Para cambiar al tema **Oscuro**:

1. En la barra de menús, seleccione **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**.

1. En la página de opciones **Entorno** > **General**, cambie la selección de **Tema de color** a **Oscuro** y, después, elija **Aceptar**.

   El tema de color para todo el IDE se cambia a **Oscuro**.

   ![Visual Studio en tema oscuro](media/quickstart-personalize-dark-theme.png)

Para obtener información sobre otras maneras de personalizar el IDE, vea [Personalizar Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>Más información

¿Quiere crear una aplicación para un teléfono iOS o Android? ¿Y un juego 3D o una aplicación habilitada para la nube? Para obtener información sobre estas y otras características de Visual Studio, vea [Características de Visual Studio 2017](../ide/advanced-feature-overview.md).

Si ya está listo para comenzar a codificar ahora, elija uno de los temas de inicio rápido de la tabla de contenido, como [Uso de Visual Studio para crear una aplicación web ASP.NET Core](quickstart-aspnet-core.md).

También puede consultar los cursos gratuitos sobre Visual Studio disponibles en [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).

## <a name="see-also"></a>Vea también

* [Más características de Visual Studio](../ide/advanced-feature-overview.md)
* [www.visualstudio.com](https://www.visualstudio.com/vs/)
* [Blog de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Descargas de Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)