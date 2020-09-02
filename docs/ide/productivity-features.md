---
title: Guía de productividad
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa4a768f8ebd8b39918fa3ba51d4eb9b3f773151
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89219769"
---
# <a name="productivity-guide-for-visual-studio"></a>Guía de productividad para Visual Studio

Si quiere ahorrar tiempo mientras escribe código, está en el lugar correcto. Esta guía de productividad incluye sugerencias que pueden ayudarle a empezar a trabajar con Visual Studio, escribir código, depurar código, controlar errores y usar métodos abreviados de teclado: todo en una sola página.

Para obtener información sobre métodos abreviados de teclado útiles, vea [Métodos abreviados de productividad](../ide/productivity-shortcuts.md). Para obtener una lista completa de accesos directos de comandos, consulte [Accesos directos de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Primeros pasos

Ahorre tiempo indagando en los menús mediante búsquedas rápidas de todo lo que necesite, como, por ejemplo, comandos, opciones de configuración, documentación y opciones de instalación. Vea los métodos abreviados de teclado de los comandos en los resultados de la búsqueda en Visual Studio para que pueda memorizarlos más fácilmente. 

- **Usar código ficticio con la lista de tareas**. Si no tiene requisitos suficientes para completar alguna parte del código, use la opción Lista de tareas para realizar un seguimiento de los comentarios de código que usan tokens tales como `TODO` y `HACK` (o tokens personalizados) y administrar los accesos directos que le llevarán directamente a una ubicación predefinida en el código. Para más información, consulte el artículo sobre el [uso de la lista de tareas](../ide/using-the-task-list.md).

- **Usar accesos directos del Explorador de soluciones**. Si no está familiarizado con Visual Studio, estos accesos directos le resultarán útiles y le ahorrarán tiempo mientras se pone al día con un nuevo código base. Para ver la lista completa de accesos directos, consulte [Métodos abreviados de teclado predeterminados de Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identificar y personalizar métodos abreviados de teclado en Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)** . Puede identificar los métodos abreviados de teclado de los comandos de Visual Studio, personalizarlos y exportarlos para que los usen otras personas. Siempre puede buscar y cambiar un método abreviado de teclado en el cuadro de diálogo Opciones.

- **Aumentar la accesibilidad en Visual Studio**. Visual Studio tiene características de accesibilidad integradas que son compatibles con los lectores de pantalla y otras tecnologías de asistencia. Consulte [Sugerencias y trucos de accesibilidad de Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) para ver la lista completa de características disponibles. 

- **Comprobar el ciclo de vida y mantenimiento del producto de Visual Studio** Para más información sobre cómo obtener actualizaciones de Visual Studio, opciones de soporte técnico para clientes empresariales y profesionales, compatibilidad con versiones anteriores de Visual Studio y componentes no cubiertos por el mantenimiento de Visual Studio, consulte [Ciclo de vida y mantenimiento del producto de Visual Studio](https://docs.microsoft.com/visualstudio/releases/2019/servicing). 

- **Instalar y administrar paquetes NuGet en Visual Studio**. La interfaz de usuario del Administrador de paquetes NuGet en Visual Studio de Windows le permite instalar, desinstalar y actualizar fácilmente paquetes NuGet en proyectos y soluciones. Para más información, consulte [Instalar y administrar paquetes en Visual Studio con el Administrador de paquetes NuGet](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Escribir código

Escriba código más rápidamente con las características siguientes.

- **Usar comandos prácticos**. Visual Studio contiene varios comandos que le ayudarán a realizar las tareas de edición comunes con mayor rapidez. Por ejemplo, puede elegir un comando para duplicar fácilmente una línea de código sin tener que copiarla, cambiar la posición del cursor y luego pegarla. Elija **Editar** > **Duplicar** o presione **Ctrl**+**E**,**V**. También puede expandir o contraer una selección de texto rápidamente; para ello, seleccione **Edición** > **Avanzado** > **Expandir selección** o **Edición** > **Avanzado** > **Contraer selección**, o bien presione **Mayús**+**Alt**+ **=** o **Mayús**+**Alt**+ **-** .

- **Usar IntelliSense**. Cuando se escribe código en el editor, aparece información de IntelliSense, como Lista de miembros, Información de parámetros, Información rápida, ayuda para las signaturas y Palabra completa. Estas características admiten la coincidencia aproximada de texto; por ejemplo, las listas de resultados para Lista de miembros no solo incluyen las entradas que comienzan con los caracteres que escribió, sino también entradas que contienen la combinación de caracteres en cualquier lugar de sus nombres. Para obtener más información, vea [Usar IntelliSense](../ide/using-intellisense.md).

- **Cambiar la inserción automática de opciones de IntelliSense mientras se escribe código**. Si se cambia IntelliSense al modo de sugerencias, se puede especificar que las opciones de IntelliSense solo se inserten si se eligen explícitamente.

     Para habilitar el modo de sugerencias, pulse las teclas **Ctrl**+**Alt**+**Barra espaciadora** o bien, en la barra de menús, elija **Editar** > **IntelliSense** > **Alternar el modo de finalización**.

- **Usar fragmentos de código**. Puede usar fragmentos de código integrados o crear sus propios fragmentos de código.

     Para insertar un fragmento de código, en la barra de menús, elija**Editar** > **IntelliSense** > **Insertar fragmento de código** o **Delimitar con**, o abra el menú contextual en un archivo y seleccione **Fragmento de código** > **Insertar fragmento de código** o **Delimitar con**. Para obtener más información, vea [Fragmentos de código](../ide/code-snippets.md).

- **Corregir errores de código alineados**. Las acciones rápidas le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción. Estas acciones se pueden aplicar con los iconos de destornillador ![icono de destornillador](media/screwdriver-icon.png) o de bombilla ![icono de bombilla](media/light-bulb-icon.png) o presionando **Alt**+**Entrar** o **Ctrl**+ **.** cuando el cursor esté en la línea de código adecuada. Para obtener más información, vea [Acciones rápidas](quick-actions.md).

- **Mostrar y editar la definición de un elemento de código**. Puede mostrar y editar rápidamente el módulo en el que se define un elemento de código, como un miembro, una variable o un valor local.

    Para abrir una definición en una ventana emergente, resalte el elemento y, después, presione las teclas **Alt**+**F12**, o abra el menú contextual del elemento y seleccione **Ver la definición**. Para abrir una definición en una ventana de código diferente, abra el menú contextual del elemento de código y, después, pulse **Ir a definición**.

- **Usar aplicaciones de ejemplo**. Puede acelerar el desarrollo de aplicaciones si descarga e instala aplicaciones de ejemplo desde [Microsoft Developer Network](https://code.msdn.microsoft.com/). También puede obtener información sobre una tecnología o un concepto de programación determinado si descarga y explora un Sample Pack para esa área.

- **Cambiar el formato de llaves con Formato/Nuevas líneas**. Use la página de opciones **Formato** para establecer opciones de formato de código en el editor de código, incluidas nuevas líneas. Para más información sobre cómo usar esta configuración en C#, consulte [Cuadro de diálogo Opciones: Editor de texto > C# > Estilo de código > Formato](../ide/reference/options-text-editor-csharp-formatting.md) Para C++, consulte el artículo sobre [establecimiento de preferencias de codificación de C++ en Visual Studio](https://docs.microsoft.com/cpp/ide/how-to-set-preferences). Para Python, consulte el artículo sobre [formato de código de Python](../python/formatting-python-code.md).

- **Cambiar la sangría por pestañas**. Utilice la configuración personalizada del editor, adaptada a cada código base, para aplicar estilos de codificación coherentes para varios desarrolladores que trabajan en un mismo proyecto en distintos editores y entornos de desarrollo integrado (IDE). Asegúrese de que todo el equipo sigue las mismas convenciones de lenguaje, convenciones de nomenclatura y reglas de formato. Dado que esta configuración personalizada es portátil y viaja con el código, puede aplicar estilos de codificación incluso fuera de Visual Studio. Para más información, consulte el artículo sobre [opciones, editor de texto, todos los lenguajes, pestañas](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Navegación dentro del código y el IDE

Puede usar diversas técnicas para buscar determinadas ubicaciones del código e ir a ellas con más rapidez. También puede cambiar el diseño de las ventanas de Visual Studio en función de sus preferencias. 

- **Establecer marcadores en líneas de código**. Puede usar marcadores para navegar rápidamente a líneas de código concretas de un archivo.

    Para establecer un marcador, en la barra de menús, pulse **Editar** > **Marcadores** > **Alternar marcador**. Puede ver todos los marcadores de una solución en la ventana **Marcadores**. Para obtener más información, vea [Establecer marcadores en el código](../ide/setting-bookmarks-in-code.md).

- **Buscar definiciones de símbolos en un archivo**. Puede buscar en una solución para encontrar definiciones de símbolos y nombres de archivo, pero los resultados de la búsqueda no incluyen espacios de nombres ni variables locales.

   Para tener acceso a esta característica, en la barra de menús, pulse **Editar** > **Navegar a**.

- **Examinar la estructura general del código**. En el **Explorador de soluciones**, puede buscar y examinar clases y sus tipos y miembros en los proyectos. También puede buscar símbolos, ver la jerarquía de llamadas de un método, buscar referencias de símbolos y realizar otras tareas. Si elige un elemento de código en el **Explorador de soluciones**, el archivo asociado se abre en una pestaña **Vista previa** y el cursor se desplaza al elemento en el archivo. Para obtener más información, vea [Visualización de la estructura del código](../ide/viewing-the-structure-of-code.md).

- **Saltar a una ubicación en un archivo con el modo de mapa**. El modo de mapa muestra líneas de código en miniatura en la barra de desplazamiento. Para más información sobre este modo de presentación, consulte [Procedimiento para Personalizar la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- **Comprender la estructura del código con un mapa de código**. Los mapas de código pueden ayudarle a visualizar las dependencias en el código y ver cómo encaja en su conjunto sin necesidad de leer archivos ni líneas de código. Para más información, vea [Map dependencies with code maps](../modeling/map-dependencies-across-your-solutions.md) (Asignar dependencias con mapas de código).

- **Consultar archivos usados con frecuencia con Editar/Ir a archivo reciente**. Use los comandos "Ir a" de Visual Studio realizan una búsqueda centrada en su código para ayudarle a encontrar rápidamente elementos específicos. Para obtener instrucciones detalladas, consulte el artículo sobre [búsqueda de código mediante comandos Ir a](../ide/go-to.md).

- **Mover la [ventana Propiedades](../ide/reference/properties-window.md) al lado derecho**. Si busca un diseño de ventana más familiar, puede mover la ventana Propiedades en Visual Studio presionando **F4**.

## <a name="find-items-faster"></a>Buscar elementos más rápido

Puede buscar comandos, archivos y opciones en el IDE, además de filtrar el contenido de las ventanas de herramientas para mostrar solo la información pertinente para la tarea actual.

- **Filtrar el contenido de las ventanas de herramientas**. Puede buscar dentro del contenido de muchas ventanas de herramientas, como el **Cuadro de herramientas**, la ventana **Propiedades** y el **Explorador de soluciones**, pero mostrar únicamente los elementos cuyos nombres contengan los caracteres que especifique.

- **Mostrar solo los errores que quiera abordar**. Si elige el selecciona el botón **Filtro** de la barra de herramientas **Lista de errores**, puede reducir el número de errores que aparecen en la ventana **Lista de errores**. Puede mostrar solo los errores de los archivos que están abiertos en el editor, solo los errores del archivo actual o solo los errores del proyecto actual. También puede buscar errores específicos dentro de la ventana **Lista de errores**.

- **Buscar cuadros de diálogo, comandos de menú, opciones y demás**. En el cuadro de búsqueda, escriba palabras clave o frases correspondientes a los elementos que intenta buscar. Por ejemplo, aparecen las opciones siguientes si escribe **nuevo proyecto**:

   ::: moniker range="vs-2017"

   ![Resultados de inicio rápido para 'nuevo proyecto'](../ide/media/productivity_quicklaunch.png)

   En **Inicio rápido** se muestran vínculos para crear un proyecto, agregar un nuevo elemento a un proyecto y a la página **Proyectos y soluciones** del cuadro de diálogo **Opciones**, entre otros. Los resultados de Inicio rápido también pueden incluir archivos de proyecto y ventanas de herramientas.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Resultados de la búsqueda para "nuevo proyecto"](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Presione **Ctrl**+**Q** para ir directamente al cuadro de búsqueda.

## <a name="debug-code"></a>Depurar código

La depuración puede consumir mucho tiempo, pero las siguientes sugerencias pueden ayudarle a acelerar el proceso.

- **Usar las herramientas del depurador de Visual Studio**. En el contexto de Visual Studio, *depurar la aplicación* normalmente significa ejecutar la aplicación en modo del depurador. El depurador ofrece muchas formas de ver lo que hace el código durante su ejecución. Consulte el artículo sobre [primer vistazo al depurador de Visual Studio](../debugger/debugger-feature-tour.md) para obtener una guía de introducción. 

- **Probar la misma página, aplicación o sitio en exploradores diferentes**. Cuando depura código, puede cambiar fácilmente entre los exploradores web instalados, incluido [Inspector de página (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), sin tener que abrir el cuadro de diálogo **Explorar con**. Puede usar la lista **Depurar destino**, que se encuentra en la barra de herramientas **Estándar** junto al botón **Iniciar depuración**, para comprobar rápidamente qué explorador está usando mientras depura o ve páginas.

    ![Selección de opciones de depuración del explorador web](../ide/media/webbrowserdropdowntoolbar.png)

- **Establecer puntos de interrupción temporales**. Puede crear un punto de interrupción temporal en la línea actual de código e iniciar el depurador simultáneamente. Al llegar a esa línea de código, el depurador activa el modo de interrupción. Para obtener más información, vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).

    Para usar esta característica, pulse las teclas **Ctrl**+**F10** o abra el menú contextual de la línea de código en la que desea establecer una interrupción y, después, elija **Ejecutar hasta el cursor**.

- **Mover el punto de ejecución durante la depuración**. Puede mover el punto de ejecución actual a otra sección de código y reiniciar la depuración a partir de ese punto. Esta técnica es útil si desea depurar una sección de código sin tener que volver a crear todos los pasos necesarios para llegar a esa sección. Para obtener más información, vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).

     Para mover el punto de ejecución, arrastre la punta de flecha amarilla hasta una ubicación donde desee establecer la siguiente instrucción en el mismo archivo de código fuente y elija la tecla **F5** para continuar con la depuración.

- **Capturar información de valor para variables**. Puede agregar una información sobre datos a una variable del código y anclarla para poder tener acceso al último valor conocido de la variable una vez finalizada la depuración. Para obtener más información, consulte [Ver valores de datos en sugerencias de datos en el editor de código](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Para agregar una Información sobre datos, el depurador debe estar en modo de interrupción. Coloque el cursor en la variable y elija el botón de anclaje en la información sobre datos que aparece. Cuando se detiene la depuración, aparece un icono azul de anclaje en el archivo de código fuente junto a la línea de código que contiene la variable. Si apunta al icono azul, aparece el valor de la variable de la sesión de depuración más reciente.

- **Borrar la ventana Inmediato**. Para borrar el contenido de la [ventana Inmediato](../ide/reference/immediate-window.md) en tiempo de diseño, escriba `>cls` o `>Edit.ClearAll`.

     Para obtener más información sobre los comandos adicionales, vea [Alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- **[Buscar cambios en el código y otro historial con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)** . CodeLens le permite averiguar qué ocurrió con el código mientras sigue centrado en su trabajo sin dejar el editor. Puede buscar referencias de una parte del código, cambios de código, errores vinculados, elementos de trabajo, revisiones de código y pruebas unitarias.

- **Usar Live Share para depurar en tiempo real con otros usuarios**. Live Share le permite editar y depurar en colaboración con otros usuarios en tiempo real, con independencia de los lenguajes de programación que use o los tipos de aplicaciones que compile. Para más información, consulte [¿Qué es Visual Studio Live Share?](https://docs.microsoft.com/visualstudio/liveshare/)

- **Usar la ventana interactiva para escribir y probar código pequeño**. Visual Studio ofrece una ventana interactiva de read–eval–print loop (REPL) que le permite escribir código arbitrario y ver resultados inmediatos. Esta forma de codificación le ayuda a aprender y experimentar con las API y las bibliotecas, así como a desarrollar de manera interactiva código de trabajo para incluirlo en sus proyectos. Para Python, consulte [Uso de la ventana interactiva de Python](../python/python-interactive-repl-in-visual-studio.md). La característica de ventana interactiva también está disponible para C#. 

## <a name="access-visual-studio-tools"></a>Acceso a Visual Studio Tools

Puede tener acceso rápidamente al Símbolo del sistema para desarrolladores o a otra herramienta de Visual Studio si ancla este elemento en el menú Inicio o en la barra de tareas.

::: moniker range="vs-2017"

1. En el Explorador de Windows, vaya a *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. En el Explorador de Windows, vaya a *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.

::: moniker-end

2. Haga clic con el botón derecho o abra el menú contextual de **Símbolo del sistema para desarrolladores** y, luego, elija **Anclar a Inicio** o **Anclar a la barra de tareas**.

## <a name="manage-files-toolbars-and-windows"></a>Administrar archivos, barras de herramientas y ventanas

En cualquier momento, puede trabajar en varios archivos de código y desplazarse entre varias ventanas de herramientas mientras desarrolla una aplicación. Para organizarse, utilice las sugerencias siguientes:

- **Mantener los archivos que usa con frecuencia visibles en el editor**. Puede anclar archivos en el lado izquierdo de la pestaña de modo que sigan siendo visibles independientemente de cuántos archivos haya abiertos en el editor.

   Para anclar un archivo, pulse la pestaña del archivo y, después, seleccione el botón **Alternar estado de anclaje**.

- **Mover documentos y ventanas a otros monitores**. Si utiliza más de un monitor al desarrollar aplicaciones, puede trabajar en algunas partes de la aplicación más fácilmente si mueve a otro monitor los archivos que están abiertos en el editor. También puede mover las ventanas de herramientas, por ejemplo las ventanas del depurador, a otro monitor y acoplar en una pestaña las ventanas de documentos y de herramientas para crear "pilas". Para obtener más información, vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   También puede administrar los archivos más fácilmente si crea otra instancia del **Explorador de soluciones** y la mueve a otro monitor. Para crear otra instancia del **Explorador de soluciones**, abra un menú contextual en el **Explorador de soluciones** y pulse **Nueva vista del Explorador de soluciones**.

- **Personalizar las fuentes que aparecen en Visual Studio**. Puede cambiar la fuente, el tamaño y el color que se usa para el texto en el IDE. Por ejemplo, puede personalizar el color de determinados elementos de código en el editor y la fuente en las ventanas de herramientas o en todo el IDE. Para obtener más información, vea [Cómo: Cambiar fuentes y colores](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) y [Cómo: Cambiar las fuentes y los colores del editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Vea también

- [Entrada de blog de sugerencias y trucos de Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Métodos abreviados de teclado predeterminados para comandos de uso frecuente](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Cómo: Personalizar menús y barras de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Tutorial: Creación de una aplicación sencilla](../get-started/csharp/tutorial-wpf.md)
- [Sugerencias y trucos de accesibilidad](../ide/reference/accessibility-tips-and-tricks.md)
