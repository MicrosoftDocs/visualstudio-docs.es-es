---
title: Corregir los errores del programa y mejorar el código
description: En este artículo se describen algunas formas básicas en las que Visual Studio puede ayudarle a encontrar y corregir problemas en el código, incluidos los errores de compilación, análisis de código, herramientas de depuración y pruebas unitarias.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49da1f46ee5e182741d3aaa56432faac39bfe0f1
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833291"
---
# <a name="make-code-work-in-visual-studio"></a>Hacer que el código funcione en Visual Studio

Visual Studio proporciona un conjunto integrado y eficaz de herramientas de compilación y depuración de proyectos. Descubra en este artículo cómo Visual Studio puede ayudarle a encontrar los problemas en el código con la salida de la compilación, análisis de código, herramientas de depuración y pruebas unitarias.

Ha ideado el editor y creado parte del código. Ahora, quiere asegurarse de que el código funciona correctamente. En Visual Studio, al igual que en la mayoría de los IDE, hay dos fases para hacer que el código funcione: compilar el código para detectar y resolver errores de proyecto y de compilador; y ejecutar el código para que encuentre errores de tiempo de ejecución y dinámicos.

## <a name="build-your-code"></a>Compilar el código

Hay dos tipos básicos de configuración de compilación: **depuración** y **lanzamiento**. La configuración de **Depuración** genera un archivo ejecutable más lento y más grande que permite una experiencia de depuración en tiempo de ejecución interactiva y más completa. Nunca se debe enviar el archivo ejecutable de **Depuración**. La configuración de **Release** crea un archivo ejecutable más rápido y optimizado, adecuado para enviar (al menos desde la perspectiva del compilador). La configuración de compilación predeterminada es **Depuración**.

La manera más sencilla de compilar el proyecto consiste en presionar **F7**, pero también se puede iniciar la compilación seleccionando **Compilar** > **Compilar solución** en el menú principal.

![Selección del menú de proyecto de compilación de Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Puede observar el proceso de compilación en la ventana de **Salida**, en la parte inferior de la interfaz de usuario de Visual Studio. Aquí se muestran los errores, las advertencias y las operaciones de compilación. Si tiene errores (o advertencias por encima de un nivel configurado), se produce un error de compilación. Puede hacer clic en los errores y advertencias para ir a la línea donde se produjeron. Recompile el proyecto presionando **F7** de nuevo (para recompilar solo los archivos con errores) o **CTRL**+**Alt**+**F7** (para realizar una recompilación limpia y completa).

Hay dos ventanas con pestañas en la ventana de resultados, debajo del editor de compilación: la ventana **Salida**, que contiene la salida sin formato del compilador (incluidos los mensajes de error), y la ventana **Lista de errores**, que proporciona una lista, que se puede ordenar y filtrar, de todos los errores y advertencias.

Cuando la compilación se realiza correctamente, verá resultados como estos en la ventana **Salida**:

![Resultados de compilación correcta de Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Revisar la lista de errores

Salvo que no haya realizado ninguna modificación en un código que ya se haya compilado correctamente, es probable que tenga un error. Si no está familiarizado con la codificación, probablemente tenga muchos. En ocasiones los errores son obvios, como un simple error de sintaxis o nombre de variable incorrecto, y a veces son difíciles de entender solo con un código críptico como guía. Para obtener una vista más clara de los problemas, vaya a la parte inferior de la ventana **Salida** de la compilación y haga clic en la pestaña **Lista de errores**. Se mostrará una vista más organizada de los errores y advertencias del proyecto, que ofrece también algunas opciones adicionales.

![Salida y lista de errores de Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Haga clic en la línea del error en la ventana **Lista de errores** para ir a la línea donde se ha producido el error. (O puede activar los números de línea si presiona **Ctrl**+**Q**, escribe **números de línea** y elige **Activar o desactivar los números de línea** en los resultados. Esta es la forma más rápida de acceder al cuadro de diálogo **Opciones** donde puede activar los números de línea).

![Editor de Visual Studio con números de línea](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opción de números de línea de Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Presione **CTRL**+**G** para ir directamente al número de línea donde se ha producido el error.

El error se identifica con un "subrayado ondulado" rojo. Mantenga el mouse sobre él para obtener más información. Al corregirlo desaparecerá, aunque pueda insertar un nuevo error con la corrección. (Esto se denomina "regresión").

![Error de Visual Studio al mantener el ratón](../ide/media/vs_ide_gs_debug_error_hover1.png)

Recorra la lista de errores y soluciónelos todos en el código.

![Ventana de errores de depuración de Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Revisar los errores con detalle

Puede que muchos errores no tengan ningún sentido expresados como están en los términos del compilador. En esos casos, necesitará información adicional. Desde la ventana **Lista de errores**, puede hacer una búsqueda automática con Bing para obtener más información sobre el error o advertencia. Haga doble clic en la línea de entrada correspondiente y seleccione **Mostrar la ayuda para el error** desde el menú contextual, o haga clic en el valor de código de error con hipervínculo en la columna **Código** de la **Lista de errores**.

![Búsqueda en Bing de lista de errores de Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Dependiendo de su configuración, el explorador web muestra los resultados de búsqueda para el código de error y el texto, o se abre una pestaña dentro de Visual Studio y muestra los resultados de búsqueda de Bing. Los resultados provienen de muchos orígenes diferentes en Internet y puede que no todos sean útiles.

## <a name="use-code-analysis"></a>Usar el análisis de código

Los analizadores de código busca problemas comunes de código que pueden dar lugar a errores en tiempo de ejecución o problemas de administración de código.

### <a name="c-and-visual-basic-code-analysis"></a>Análisis de código de C# y Visual Basic

Visual Studio incluye un conjunto integrado de [analizadores de .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) que examinan el código de C# y Visual Basic mientras escribe. Puede instalar analizadores adicionales como una extensión de Visual Studio, o como un paquete de NuGet. Si se detectan infracciones de reglas, se indican tanto en la lista de errores como en el editor de código con un subrayado ondulado bajo el código incorrecto.

### <a name="c-code-analysis"></a>Análisis de código de C++

Para analizar el código de C++, ejecute el [análisis de código estático](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Adquiera el hábito de ejecutarlo después de limpiar los errores evidentes que impiden que se realice correctamente la compilación, y dedique algún tiempo a solucionar las advertencias que se puedan producir. Se ahorrará algunos dolores de cabeza y aprenderá algunas técnicas de estilo de código.

Presione **Alt**+**F11** (o seleccione **Analizar** > **Ejecutar análisis de código en la solución** en el menú superior) para iniciar el análisis de código estático.

![Elemento de menú Análisis de código de Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Las advertencias nuevas o actualizadas se muestran en la pestaña **Lista de errores**, en la parte inferior del IDE. Haga clic en las advertencias para ir directamente a ellas en el código.

![Lista de errores con advertencias de Visual Studio](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Uso de Acciones rápidas para corregir o refactorizar el código

Las [acciones rápidas](../ide/quick-actions.md), que están disponibles desde el icono de la bombilla o el destornillador, le permiten refactorizar código alineado. Son una manera fácil de corregir advertencias comunes de forma rápida y eficaz en el código de C#, C++ y Visual Basic. Para obtener acceso a ellas, haga clic con el botón derecho en un subrayado ondulado de advertencia y seleccione **Acciones rápidas y refactorizaciones**. O bien, cuando el cursor se encuentre en la línea con el subrayado ondulado de color, presione **Ctrl**+ **.** o bien, haga clic en el icono de la bombilla, la bombilla de error o el destornillador en el margen. Verá una lista de posibles correcciones o refactorizaciones que puede aplicar a esa línea de código.

![Vista previa de bombilla de Visual Studio](../ide/media/quick-actions-options.png)

Las acciones rápidas pueden usarse siempre que los analizadores de código determinen que hay una posibilidad de corregir, refactorizar o mejorar el código. Haga clic en cualquier línea de código, haga clic con el botón derecho para abrir el menú contextual y seleccione **Acciones rápidas y refactorizaciones**. Si hay opciones disponibles de refactorización o de mejora, se muestran. En caso contrario, se mostrará el mensaje **No hay disponibles acciones rápidas aquí** en la esquina inferior izquierda del IDE.

![Texto de No hay disponibles acciones rápidas](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Con experiencia, puede usar rápidamente las teclas de dirección y **CTRL**+ **.** para comprobar si hay posibilidades fáciles de refactorización y limpiar el código.

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Ejecución de la limpieza de código

Visual Studio proporciona el [formato a petición del archivo de código de C#](code-styles-and-code-cleanup.md#apply-code-styles), incluidas las preferencias de estilo de código, mediante el botón **Limpieza de código** de la parte inferior del editor.

![Botón Limpieza de código de Visual Studio 2019](media/execute-code-cleanup.png)

Además de aplicar al archivo formato de espacios, sangrías, guiones, etc., la **limpieza de código** también aplica un conjunto de convenciones de estilo de código que usted defina. Sus preferencias para cada estilo de código se leen en el [archivo EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), si dispone de uno para el proyecto, o desde la [configuración de estilo de código](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) en el cuadro de diálogo **Opciones**.

::: moniker-end

## <a name="debug-your-running-code"></a>Depurar el código en ejecución

Ahora que ha compilado el código correctamente y ha realizado un poco de limpieza, ejecútelo presionando **F5** o seleccionando **Depuración** > **Iniciar depuración**. La aplicación se inicia en un entorno de depuración para que pueda observar su comportamiento con detalle. El IDE de Visual Studio cambia mientras la aplicación se está ejecutando: la ventana **Salida** se sustituye por dos nuevas (en la configuración de ventanas predeterminada), que son las ventanas con pestañas **Automático/Variables locales/Inspección** y **Pila de llamadas/Puntos de interrupción/Configuración de excepciones/Salida**. Estas ventanas tienen varias pestañas que permiten inspeccionar y evaluar las variables, los subprocesos, las pilas de llamadas y otros comportamientos de la aplicación mientras se ejecuta.

![Ventanas Automático y Pila de llamadas de Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Detenga la aplicación presionando **Mayús**+**F5** o haciendo clic en el botón **Detener**. O bien, simplemente cierre la ventana principal de la aplicación (o el cuadro de diálogo de línea de comandos).

Si el código se ejecuta perfectamente y tal y como se esperaba, ¡enhorabuena! En cambio, si ha dejado de responder, se ha bloqueado o dio resultados extraños, necesitará encontrar el origen de esos problemas y corregir los errores.

### <a name="set-simple-breakpoints"></a>Establecer puntos de interrupción simples

Los [puntos de interrupción](../debugger/using-breakpoints.md) son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. No es necesario recompilar un proyecto después de establecer y quitar puntos de interrupción.

Para establecer un punto de interrupción, haga clic en el margen más alejado de la línea en la que quiere que se produzca la interrupción, o bien presione **F9** para establecer un punto de interrupción en la línea de código actual. Al ejecutar el código, se detendrá (o *interrumpirá*) antes de que se ejecuten las instrucciones de esta línea de código.

![Punto de interrupción de Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Entre los usos habituales de los puntos de interrupción se incluyen:

- Para acotar el origen de un bloqueo o de un programa que no responde, disperse los puntos de interrupción por todo el código de la llamada a métodos que crea que está causando el error. Mientras ejecuta el código en el depurador, quite y restablezca los puntos de interrupción más próximos entre sí hasta que encuentre la línea de código incorrecta. Vea la sección siguiente para obtener información sobre cómo ejecutar código en el depurador.

- Cuando introduzca código nuevo, establezca un punto de interrupción al inicio del mismo y ejecute el código para asegurarse de que se comporta tal y como se espera.

- Si ha implementado un comportamiento complejo, establezca puntos de interrupción para el código algorítmico de modo que pueda inspeccionar los valores de las variables y los datos cuando el programa se interrumpa.

- Si está escribiendo código de C o C++, use puntos de interrupción para detener el código y poder inspeccionar los valores de dirección (busque NULL) y los recuentos de referencias al depurar errores relacionados con la memoria.

Para más información sobre el uso de puntos de interrupción, vea [Usar puntos de interrupción](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Inspeccionar el código en tiempo de ejecución

Cuando el código en ejecución llega a un punto de interrupción y se detiene, la línea de código marcada en amarillo (la instrucción actual) todavía no se ha ejecutado. En este momento, es posible que quiera ejecutar la instrucción actual y después inspeccionar los valores cambiados. Se pueden usar varios comandos de *paso* para ejecutar código en el depurador. Si el código marcado es una llamada de método, puede ejecutarlo paso a paso si presiona **F11**. También se puede *saltar* la línea de código presionando **F10**. Para ver los comandos adicionales y obtener detalles sobre cómo recorrer el código, lea [Navegar por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).

![Captura de pantalla de la ventana de código de Visual Studio. Un punto rojo en el margen izquierdo indica un punto de interrupción en la línea de código resaltada en amarillo.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

En la ilustración anterior, puede avanzar una instrucción en el depurador presionando **F10** o **F11** (dado que no hay ninguna llamada de método, ambos comandos tienen el mismo resultado).

Cuando el depurador está pausado, puede inspeccionar las variables y pilas de llamadas para determinar qué está sucediendo. ¿Los valores están dentro de los intervalos que esperaba? ¿Las llamadas se están realizando en el orden correcto?

![Captura de pantalla de la ventana de código de Visual Studio. En la línea de código resaltada en amarillo, hay una variable seleccionada y una lista desplegable muestra su valor actual y sus referencias.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Mantenga el mouse sobre una variable para ver su valor actual y las referencias. Si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o en el código que realiza la llamada. Para obtener información sobre depuración más detallada, [vea más información](../debugger/debugger-feature-tour.md) sobre cómo usar el depurador.

Además, Visual Studio muestra la ventana **Herramientas de diagnóstico**, donde puede observar el uso que hace la aplicación de la memoria y la CPU con el tiempo. Más adelante en el desarrollo de aplicaciones, puede usar estas herramientas para buscar un uso elevado de la CPU inesperado o de asignación de memoria. Úsela con la ventana **Inspección** y con puntos de interrupción para determinar qué está causando un uso intensivo o problemas de liberación de recursos inesperados. Para más información, vea [Guía de características de generación de perfiles](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

Las pruebas unitarias son la primera línea de defensa contra errores de código porque, cuando se realizan correctamente, se prueba una sola "unidad" de código (normalmente una sola función) y son más fáciles de depurar que el programa completo. Visual Studio instala los marcos de pruebas unitarias de Microsoft tanto para código administrado como nativo. Use un entorno de pruebas unitarias para crear pruebas unitarias, ejecutarlas y notificar los resultados de las mismas. Cuando realice cambios, vuelva a ejecutar las pruebas unitarias para probar que el código sigue funcionando correctamente. Con Visual Studio Enterprise, puede ejecutar las pruebas automáticamente después de cada compilación.

Para empezar, lea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Para obtener más información sobre las pruebas unitarias en Visual Studio y cómo pueden ayudarle a crear código de mejor calidad, lea [Conceptos básicos de las pruebas unitarias](../test/unit-test-basics.md).

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Más información sobre cómo usar el depurador](../debugger/index.yml)
- [Generación y corrección del código](../ide/code-generation-in-visual-studio.md)
