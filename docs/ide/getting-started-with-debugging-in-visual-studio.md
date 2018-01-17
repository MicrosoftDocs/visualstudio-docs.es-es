---
title: "Introducción a la depuración en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c75b5508cd23a2131bcdd64cf52aacc1486d2713
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="get-started-with-debugging-in-visual-studio"></a>Introducción a la depuración en Visual Studio
Visual Studio proporciona un conjunto integrado y eficaz de herramientas de compilación y depuración de proyectos. En este tema verá cómo empezar a usar el conjunto más básico de características de depuración de la interfaz de usuario.  

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>Mi código no funciona. ¡Ayuda, Visual Studio!  
 Ha ideado el editor y ha creado parte del código. Ahora, quiere empezar a depurar ese código. En Visual Studio, al igual que en la mayoría de los IDE, hay dos fases de depuración: compilar el código para detectar y resolver errores de proyecto y de compilador; y ejecutar ese código en el entorno para detectar y resolver errores de tiempo de ejecución y dinámicos.  

### <a name="build-your-code"></a>Compilar el código  
 Hay dos tipos básicos de configuración de compilación: **Depuración** y **Versión**. La primera configuración genera un archivo ejecutable más lento y más grande que permite una experiencia de depuración en tiempo de ejecución interactiva y más completa, pero que nunca se debe enviar. La segunda crea un archivo ejecutable más rápido y optimizado, adecuado para enviar (al menos desde la perspectiva del compilador). La configuración de compilación predeterminada es **Depuración**.

La manera más sencilla de compilar el proyecto consiste en presionar **F7**, pero también se puede iniciar la compilación seleccionando **Compilar > Compilar solución** en el menú principal.  

 ![Selección del menú del proyecto de compilación de Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 Puede observar el proceso de compilación en la ventana de estado **Salida**, en la parte inferior de la interfaz de usuario de Visual Studio. Aquí se muestran los errores, las advertencias y las operaciones de compilación. Si tiene errores (o advertencias por encima de un nivel configurado), se producirá un error de compilación. Puede hacer clic en los errores y advertencias para ir a la línea donde se produjeron. Recompile el proyecto presionando **F7** de nuevo (para recompilar solo los archivos con errores) o **Ctrl+Alt+F7** (para realizar una recompilación limpia y completa).  

 Hay dos ventanas de compilación con pestañas en la ventana de resultados, debajo del editor de compilación: la ventana **Salida**, que contiene la salida sin formato del compilador (incluidos los mensajes de error), y la ventana **Lista de errores**, que proporciona una lista, que se puede ordenar y filtrar, de todos los errores y advertencias.  

 Cuando se realiza correctamente, verá resultados como estos en la ventana **Salida**.  

 ![Salida de compilación correcta de Visual Studio](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="review-the-error-list"></a>Revisar la lista de errores  
 Salvo que no haya realizado ninguna modificación en un código que ya se haya compilado correctamente, es probable que tenga un error. Si no está familiarizado con la codificación, probablemente tenga muchos. En ocasiones los errores son obvios, como un simple error de sintaxis o nombre de variable incorrecto, y a veces son difíciles de entender solo con un código críptico como guía. Para obtener una vista más clara de los problemas, vaya a la parte inferior de la ventana **Salida** de la compilación y haga clic en la pestaña **Lista de errores**. Se mostrará una vista más organizada de los errores y advertencias del proyecto, que ofrece también algunas opciones adicionales.  

 ![Lista de errores y salida de Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 Haga clic en la línea del error en la ventana **Lista de errores** para ir a la línea donde se ha producido el error. (O active los números de línea; para ello, haga clic en la barra **Inicio rápido** en la parte superior derecha, escriba "números de línea" y presione Entrar. Esta es la forma más rápida de acceder a la entrada de la ventana **Opciones** donde puede activar los números de línea. Obtenga información sobre cómo usar la barra **Inicio rápido** y ahórrese muchos clics en la interfaz de usuario).  

 ![Editor de Visual Studio con números de línea](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Opción de números de línea de Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 Presione **Ctrl+G** para ir directamente al número de línea donde se ha producido el error.  

 El error se identifica con un "subrayado ondulado" rojo. Mantenga el mouse sobre él para obtener más información. Al corregirlo desaparecerá, aunque pueda insertar un nuevo error con la corrección. (Esto se denomina "regresión").  

 ![Error de Visual Studio al mantener el mouse](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 Recorra la lista de errores y soluciónelos todos en el código.  

 ![Ventana de errores de depuración de Visual Studio](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="review-errors-in-detail"></a>Revisar los errores con detalle  
 Puede que muchos errores no tengan ningún sentido expresados como están en los términos del compilador. En esos casos, necesitará información adicional. En la ventana **Lista de errores**, puede hacer una búsqueda automática con Bing para obtener más información sobre el error (o advertencia); para ello, haga clic con el botón derecho en la línea de entrada correspondiente y seleccione **Ayuda para Mostrar mensaje** en el menú contextual.  

 ![Búsqueda en Bing de lista de errores de Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 Se abre una pestaña en Visual Studio que hospeda los resultados de una búsqueda de Bing para el código y el texto del error. Los resultados provienen de muchos orígenes diferentes en Internet y puede que no todos sean útiles.  

 Como alternativa, puede hacer clic en el valor de código de error con hipervínculo en la columna **Código** de la **Lista de errores**. Se iniciará una búsqueda de Bing solo del código de error.  

### <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Usar bombillas para corregir o refactorizar el código  
 Las bombillas son una característica nueva de Visual Studio que permiten refactorizar código alineado. Son una manera fácil de corregir advertencias comunes de forma rápida y eficaz. Para obtener acceso a ellas, haga clic con el botón derecho en un subrayado ondulado de advertencia (o presione **Ctrl+**. manteniendo el mouse sobre la línea ondulada) y, después, seleccione **Acciones rápidas**.  

 ![Opciones rápidas de bombilla de Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 Verá una lista de posibles correcciones o refactorizaciones que puede aplicar a esa línea de código.  

 ![Vista previa de bombilla de Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 Las bombillas puede usarse siempre que los analizadores de código determinan que hay una posibilidad de corregir, refactorizar o mejorar el código. Haga clic en cualquier línea de código, haga clic con el botón derecho para abrir el menú contextual y seleccione **Acciones rápidas** (o bien, si prefiere la eficacia, presione **Ctrl+**.). Si hay disponibles opciones de refactorización o mejora, se mostrarán; de lo contrario, se mostrará el mensaje `No quick options available here` en la esquina inferior izquierda del IDE.  

 ![Texto "no opción" de bombilla de Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 Con experiencia, puede usar rápidamente las teclas de dirección y **Ctrl+**. para comprobar si hay posibilidades de refactorización con las opciones rápidas y limpiar el código.  

 Para obtener más información sobre las bombillas, vea [Realizar acciones rápidas con las bombillas](../ide/perform-quick-actions-with-light-bulbs.md).  

### <a name="debug-your-running-code"></a>Depurar el código en ejecución  
 Ahora que ha compilado el código correctamente y ha realizado un poco de limpieza, ejecútelo presionando **F5** o seleccionando **Depuración > Iniciar depuración**. La aplicación se iniciará en un entorno de depuración para que pueda observar su comportamiento con detalle. El IDE de Visual Studio cambia mientras la aplicación se está ejecutando: la ventana **Salida** se sustituye por dos nuevas (en la configuración de ventanas predeterminada), que son las ventanas con pestañas **Automático/Variables locales/Inspección** y **Pila de llamadas/Puntos de interrupción/Configuración de excepciones/Salida**. Estas ventanas tienen varias pestañas que permiten inspeccionar y evaluar las variables, los subprocesos, las pilas de llamadas y otros comportamientos de la aplicación mientras se ejecuta.  

 ![Ventanas automáticas y de pila de llamadas de Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 Puede detener la aplicación presionando **Mayús+F5** o haciendo clic en el botón **Detener**. O bien, simplemente cierre la ventana principal de la aplicación (o el cuadro de diálogo de línea de comandos).  

 Si el código se ejecuta perfectamente y tal y como se esperaba, ¡enhorabuena! En cambio, si ha dejado de responder o se ha bloqueado, o dio resultados extraños, necesitará encontrar el origen de esos problemas y corregir los errores.  

### <a name="set-simple-breakpoints"></a>Establecer puntos de interrupción simples  
 Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. No es necesario recompilar un proyecto después de establecer y quitar puntos de interrupción.  

 Para establecer un punto de interrupción, haga clic en el margen más alejado de la línea en la que quiere que se produzca la interrupción, o bien presione **F9** para establecer un punto de interrupción en la línea de código actual. Al ejecutar el código, se detendrá (o *interrumpirá*) antes de que se ejecuten las instrucciones de esta línea de código.  

 ![Punto de interrupción de Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")   

 Entre los usos habituales de los puntos de interrupción se incluyen:  

1.  Para reducir el origen de un bloqueo, dispérselos por todo el código de la llamada a métodos que crea que está causando el error. Mientras ejecuta el código en el depurador, quite y restablezca los puntos de interrupción más próximos entre sí hasta que encuentre la línea de código incorrecta.  Vea la sección siguiente para obtener información sobre cómo ejecutar código en el depurador.

2.  Cuando introduzca código nuevo, establezca un punto de interrupción al inicio del mismo y ejecute el código para asegurarse de que se comporta tal y como se espera.

3.  Si ha implementado un comportamiento complejo, establezca puntos de interrupción para el código algorítmico de modo que pueda inspeccionar los valores de las variables y los datos cuando el programa se interrumpa.  

4.  Si está escribiendo código de C o C++, use puntos de interrupción para detener el código y poder inspeccionar los valores de dirección (busque NULL) y los recuentos de referencias al depurar errores relacionados con la memoria.  

 Para más información sobre el uso de puntos de interrupción, vea [Usar puntos de interrupción](../debugger/using-breakpoints.md).  

### <a name="inspect-your-code-at-run-time"></a>Inspeccionar el código en tiempo de ejecución  
 Cuando el código en ejecución llega a un punto de interrupción y se detiene, la línea de código marcada en amarillo (la instrucción actual) todavía no se ha ejecutado. En este momento, es posible que quiera ejecutar la instrucción actual y después inspeccionar los valores cambiados. Se pueden usar varios comandos de *paso* para ejecutar código en el depurador. Si el código marcado es una llamada de método, puede ejecutarlo paso a paso si presiona **F11**. También se puede *saltar* la línea de código presionando **F10**. Para ver los comandos adicionales y obtener detalles sobre cómo recorrer el código, lea [Navegar por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).

 ![Inspección del valor de tiempo de ejecución de Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.PNG "vs_ide_gs_debug_inspect_value") 

 En la ilustración anterior, puede avanzar una instrucción en el depurador presionando **F10** o **F11** (dado que no hay ninguna llamada de método, ambos comandos tienen el mismo resultado).

 Cuando el depurador está pausado, puede inspeccionar las variables y pilas de llamadas para determinar qué está sucediendo. ¿Los valores están dentro de los intervalos que esperaba? ¿Las llamadas se están realizando en el orden correcto?  

 ![Inspección del valor de tiempo de ejecución de Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 Mantenga el mouse sobre una variable para ver los valores y las referencias que contiene actualmente. Si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o en las líneas de código que realizan la llamada.  Para obtener información más detallada, [vea más información](../debugger/getting-started-with-the-debugger.md) sobre cómo usar el depurador. 

 Además, Visual Studio muestra la ventana Herramientas de diagnóstico, donde puede observar el uso que hace la aplicación de la memoria y la CPU con el tiempo. Más adelante en el desarrollo de aplicaciones, puede usar estas herramientas para buscar un uso elevado de la CPU inesperado o de asignación de memoria. Úsela con la ventana **Inspección** y con puntos de interrupción para determinar qué está causando un uso intensivo o problemas de liberación de recursos inesperados.  Para más información, vea [Guía de características de generación de perfiles](../profiling/profiling-feature-tour.md).

### <a name="run-unit-tests"></a>Ejecutar pruebas unitarias  
 Las pruebas unitarias son la primera línea de defensa contra errores de código porque, cuando se realizan correctamente, se prueba una sola "unidad" de código (normalmente una sola función) y suelen ser mucho más fáciles de depurar que la depuración del programa completo. Visual Studio instala los marcos de pruebas unitarias de Microsoft tanto para código administrado como nativo. Use un entorno de pruebas unitarias para crear pruebas unitarias, ejecutarlas y notificar los resultados de las mismas. Cuando realice cambios, vuelva a ejecutar las pruebas unitarias para probar que el código sigue funcionando correctamente. Si usa la edición de Visual Studio Enterprise, puede ejecutar las pruebas automáticamente después de cada compilación.  

 Para empezar, lea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  

 Para obtener más información sobre las pruebas unitarias en Visual Studio y cómo pueden ayudarle a crear código de mejor calidad, lea [Conceptos básicos de las pruebas unitarias](../test/unit-test-basics.md).  

### <a name="perform-static-code-analysis"></a>Realizar análisis de código estático  
 "Análisis estático de código" es una manera sofisticada de decir "comprobar automáticamente si mi código tiene problemas comunes que pueden producir errores en tiempo de ejecución o problemas de administración de código". Adquiera el hábito de ejecutarlo después de limpiar los errores evidentes que impedían la compilación, y dedique algún tiempo a solucionar las advertencias que se puedan producir. Se ahorrará algunos dolores de cabeza y aprenderá algunas técnicas de estilo de código.  

 Presione **Alt+F11** (o seleccione **Analizar > Ejecutar análisis de código en la solución** en el menú superior) para iniciar el análisis de código estático. Puede llevar algún tiempo si tiene mucho código.  

 ![Elemento de menú de análisis de código en Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 Las advertencias nuevas o actualizadas se mostrarán en la pestaña **Lista de errores**, en la parte inferior del IDE. Haga clic en las advertencias para ir directamente a ellas.  

 ![Lista de errores de Visual Studio con advertencias](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  

 Las advertencias se identifican por un subrayado ondulado de verde amarillento brillante en lugar de un subrayado rojo. Mantenga el mouse sobre ellas para obtener más información y haga clic con el botón secundario en ellas para obtener un menú contextual con opciones de corrección o refactorización.  

 ![Advertencia de análisis de código de Visual Studio al mantener el mouse](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

## <a name="see-also"></a>Vea también  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)  
 [Más información sobre cómo usar el depurador](../debugger/getting-started-with-the-debugger.md)
