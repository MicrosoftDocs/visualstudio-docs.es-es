---
title: Introducción a la depuración en Visual Studio 2015 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ec46ba094ccafbb06ec64e181d4a64906feaa205
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581129"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Introducción a la depuración en Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cómo empezar a depurar en Visual Studio](https://docs.microsoft.com/visualstudio/ide/getting-started-with-debugging-in-visual-studio).  
  
Visual Studio 2015 proporciona un conjunto integrado y eficaz de herramientas de compilación y depuración de proyectos. En este tema verá cómo empezar a usar el conjunto más básico de características de depuración de la interfaz de usuario.  
  
 Nota: los vínculos a características más avanzadas y a temas específicos de la plataforma (o característica) están en la parte inferior de esta página.  
  
## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mi código no funciona. ¡Ayuda, Visual Studio 2015!  
 Ha ideado el editor y ha creado parte del código. Ahora, quiere empezar a depurar ese código. En Visual Studio 2015, al igual que en la mayoría de los IDE, hay dos fases de depuración: compilar el código para detectar y resolver errores de proyecto y de compilador; y ejecutar ese código en el entorno para detectar y resolver errores de tiempo de ejecución y dinámicos.  
  
### <a name="configuring-a-build"></a>Configurar una compilación  
 Hay dos tipos básicos de configuración de compilación: **Depuración** y **Versión**. La primera configuración genera un archivo ejecutable más lento y más grande que permite una experiencia de depuración en tiempo de ejecución interactiva y más completa, pero que nunca se debe enviar. La segunda crea un archivo ejecutable más rápido y optimizado, adecuado para enviar (al menos desde la perspectiva del compilador).  
  
 La configuración de compilación predeterminada es **Depuración**.  
  
 ![Botón de compilación de depuración de Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")  
  
 También puede especificar una plataforma de compilación de destino específica, como **x86** (CPU Intel de 32 bits), **x64** (CPU Intel de 64 bits) y **ARM** (CPU ARM; solo se admite para ciertos tipos de aplicación). El valor predeterminado es **x86** para proyectos administrados y nativos. Para cambiarlo, haga clic en la lista desplegable de plataforma de compilación y seleccione una plataforma diferente o **Administrador de configuración...**  
  
 ![Ventana del Administrador de archivos de configuración de Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")  
  
 Puede especificar la configuración de compilación de destino mediante el **Administrador de configuración**. Inícielo, haga clic en la lista desplegable **Configuración** o **CPU** y seleccione **Nueva...** para crear una nueva compilación o plataforma.  
  
 ![Ventana del Administrador de configuración de Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")  
  
 Para empezar, use **Depuración** y **x86** como configuración de compilación y plataforma, respectivamente. Cuando haya terminado la codificación y la depuración, cambie la configuración a **Versión** y elija una plataforma de destino específica. (Las versiones anteriores de Visual Studio proporcionan una plataforma predeterminada **AnyCPU** para los proyectos de código de .NET).  
  
 Nota: al compilar un proyecto, se usan también los valores de configuración y plataforma para determinar la ruta de acceso al directorio del proyecto que se creará para almacenar el archivo ejecutable. Normalmente, esta es **\<ruta-al-proyecto>\\<nombre-proyecto>\\<configuración\>\\<plataforma\>**. Por ejemplo, un proyecto con una configuración de `Debug` y una plataforma de `x86` se encontraría en `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Esto puede ser útil si tiene sus propias herramientas o scripts que administran estos ejecutables compilados.  
  
### <a name="building-your-code"></a>Compilar el código  
 Una vez configurada la compilación, es el momento de compilar el proyecto. La manera más sencilla de hacerlo es presionar F7, pero también puede iniciar la compilación seleccionando **Compilar->Compilar solución** en el menú principal.  
  
 ![Selección del menú del proyecto de compilación de Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")  
  
 Puede observar el proceso de compilación en la ventana de estado **Salida**, en la parte inferior de la interfaz de usuario de Visual Studio. Aquí se muestran los errores, las advertencias y las operaciones de compilación. Si tiene errores (o advertencias por encima de un nivel configurado), se producirá un error de compilación. Puede hacer clic en los errores y advertencias para ir a la línea donde se produjeron. Recompile el proyecto presionando **F7** de nuevo (para recompilar solo los archivos con errores) o **Ctrl+Alt+F7** (para realizar una recompilación limpia y completa).  
  
 Hay dos ventanas de compilación con pestañas en la ventana de resultados, debajo del editor de compilación: la ventana **Salida**, que contiene la salida sin formato del compilador (incluidos los mensajes de error), y la ventana **Lista de errores**, que proporciona una lista, que se puede ordenar y filtrar, de todos los errores y advertencias.  
  
 Cuando se realiza correctamente, verá resultados como estos en la ventana **Salida**.  
  
 ![Salida de compilación correcta de Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")  
  
### <a name="reviewing-the-error-list"></a>Revisar la lista de errores  
 Salvo que no haya realizado ninguna modificación en un código que ya se haya compilado correctamente, es probable que tenga un error. Si no está familiarizado con la codificación, probablemente tenga muchos. Los errores a veces son obvios, como un simple error de sintaxis o nombre de variable incorrecto, y a veces son difíciles de entender solo con un código críptico como guía. Para obtener una vista más clara de los problemas, vaya a la parte inferior de la ventana **Salida** de la compilación y haga clic en la pestaña **Lista de errores**. Se mostrará una vista más organizada de los errores y advertencias del proyecto, que ofrece también algunas opciones adicionales.  
  
 ![Lista de errores y de salida de Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")  
  
 Haga clic en la línea del error en la ventana **Lista de errores** para ir a la línea donde se ha producido el error. (O active los números de línea; para ello, haga clic en la barra **Inicio rápido** en la parte superior derecha, escriba "números de línea" y presione Entrar. Esta es la forma más rápida de acceder a la entrada de la ventana **Opciones** donde puede activar los números de línea. Obtenga información sobre cómo usar la barra **Inicio rápido** y ahórrese muchos clics en la interfaz de usuario).  
  
 ![Editor de Visual Studio con números de línea](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")  
  
 ![Opción de números de línea de Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")  
  
 Use Ctrl+G para ir directamente al número de línea donde se ha producido el error.  
  
 El error se identifica con un subrayado ondulado rojo. Mantenga el mouse sobre él para obtener más información. Al corregirlo desaparecerá, aunque pueda insertar un nuevo error con la corrección. (Esto se denomina "regresión").  
  
 ![Error de Visual Studio al mantener el mouse](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")  
  
 Recorra la lista de errores y soluciónelos todos en el código.  
  
 ![Ventana de errores de depuración de Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")  
  
### <a name="reviewing-errors-in-detail"></a>Revisar los errores con detalle  
 Puede que muchos errores no tengan ningún sentido expresados como están en los términos del compilador. En esos casos, necesitará información adicional. En la ventana **Lista de errores**, puede hacer una búsqueda automática con Bing para obtener más información sobre el error (o advertencia); para ello, haga clic con el botón derecho en la línea de entrada correspondiente y seleccione **Ayuda para Mostrar mensaje** en el menú contextual.  
  
 ![Búsqueda en Bing de lista de errores de Visual Studio](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")  
  
 Se abre una pestaña en la Visual Studio 2015 que contiene los resultados de Bing para el código y el texto del error. Los resultados provienen de muchos orígenes diferentes en Internet y puede que no todos sean útiles.  
  
 Como alternativa, puede hacer clic en el valor de código de error con hipervínculo en la columna **Código** de la **Lista de errores**. Se iniciará una búsqueda de Bing solo del código de error.  
  
### <a name="performing-static-code-analysis"></a>Realizar análisis estáticos de código  
 "Análisis estático de código" es una manera sofisticada de decir "comprobar automáticamente si mi código tiene problemas comunes que pueden producir errores en tiempo de ejecución o problemas de administración de código". Adquiera el hábito de ejecutarlo después de limpiar los errores evidentes que impedían la compilación, y dedique algún tiempo a solucionar las advertencias que se puedan producir. Se ahorrará algunos dolores de cabeza y aprenderá algunas técnicas de estilo de código.  
  
 Presione Alt+F11 (o seleccione **Analizar->Ejecutar análisis de código en la solución** en el menú superior) para iniciar el análisis estático de código. Puede llevar algún tiempo si tiene mucho código.  
  
 ![Elemento de menú de Visual Studio 2015 Code Analysis](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")  
  
 Las advertencias nuevas o actualizadas se mostrarán en la pestaña **Lista de errores**, en la parte inferior del IDE. Haga clic en las advertencias para ir directamente a ellas.  
  
 ![Lista de errores de Visual Studio 2015 con advertencias](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  
  
 Las advertencias se identifican por un subrayado ondulado de verde amarillento brillante en lugar de un subrayado rojo. Mantenga el mouse sobre ellas para obtener más información y haga clic con el botón secundario en ellas para obtener un menú contextual con opciones de corrección o refactorización.  
  
 ![Advertencia de análisis de código de Visual Studio al mantener el mouse](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  
  
### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Usar bombillas para corregir o refactorizar código  
 Las bombillas son una característica nueva de Visual Studio 2015 que permiten refactorizar código alineado. Son una manera fácil de corregir advertencias comunes de forma rápida y eficaz. Para acceder a ellas, haga clic con el botón derecho en un subrayado ondulado de advertencia (o presione Ctrl+. manteniendo el mouse sobre la línea ondulada) y, después, seleccione **Acciones rápidas**.  
  
 ![Opciones rápidas de Visual Studio 2015 bombilla](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")  
  
 Verá una lista de posibles correcciones o refactorizaciones que puede aplicar a esa línea de código.  
  
 ![Preview Visual Studio 2015 bombilla](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  
  
 Las bombillas puede usarse siempre que los analizadores de código determinan que hay una posibilidad de corregir, refactorizar o mejorar el código. Haga clic en cualquier línea de código, haga clic con el botón derecho para abrir el menú contextual y seleccione **Opciones rápidas** (o bien, si prefiere la eficacia, presione Ctrl+.). Si hay disponibles opciones de refactorización o mejora de área, se mostrarán; de lo contrario, se mostrará el mensaje `No quick options available here` en la esquina inferior izquierda del IDE.  
  
 ![Visual Studio 2015 bombilla "no opción" texto](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  
  
 Con experiencia, puede usar rápidamente las teclas de dirección y Ctrl+. para comprobar si hay posibilidades de refactorización con las opciones rápidas y limpiar el código.  
  
 Para obtener más información sobre las bombillas, vea [Realizar acciones rápidas con las bombillas](../ide/perform-quick-actions-with-light-bulbs.md).  
  
### <a name="debugging-your-running-code"></a>Depurar el código en ejecución  
 Ahora que ha compilado el código correctamente y ha realizado un poco de limpieza, ejecútelo presionando F5 o seleccionando **Depuración->Iniciar depuración**. La aplicación se iniciará en un entorno de depuración para que pueda observar su comportamiento con detalle. El IDE de Visual Studio 2015 cambia mientras se ejecuta la aplicación: el **salida** ventana se sustituye por dos nuevas (en la configuración de ventanas predeterminada), el **automático/variables locales/módulos/inspección** ventana con pestañas y el **Llamadas o los puntos de interrupción/pila de una excepción de configuración/salida** ventana con pestañas. Estas ventanas tienen varias pestañas que permiten inspeccionar y evaluar las variables, los subprocesos, las pilas de llamadas y otros comportamientos de la aplicación mientras se ejecuta.  
  
 ![VS2015 Automático y llame a la pila Windows](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  
  
 Pruebe distintas acciones con la aplicación y observe los cambios. Si algo parece anómalo, pause la aplicación presionando Ctrl+Alt+Interrumpir (o haga clic en el botón **Pausar**).  
  
 ![Botón Interrumpir todo de Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")  
  
 Presione F5 para continuar la ejecución de la aplicación (o haga clic en el botón **Continuar**).  
  
 ![Botón Continuar depuración de Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")  
  
 Puede detener la aplicación presionando Mayús+F5 o haciendo clic en el botón **Detener**. O bien, simplemente cierre la ventana principal de la aplicación (o el cuadro de diálogo de línea de comandos).  
  
 Si el código se ejecuta perfectamente y tal y como se esperaba, ¡enhorabuena! Cambie la configuración de compilación a **Versión** y recompílela para su implementación. (Los profesionales quizás quieran pasar a las pruebas unitarias al final). Sin embargo, si dejó de responder o se bloqueó, o dio resultados extraños, necesitará encontrar el origen de esos problemas y corregir los errores.  
  
### <a name="setting-simple-breakpoints"></a>Establecer puntos de interrupción simples  
 Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. No es necesario recompilar un proyecto después de establecer y quitar puntos de interrupción.  
  
 Para establecer un punto de interrupción, haga clic en el margen más alejado de la línea en la que quiere que se produzca la interrupción, o seleccione la línea de código y presione F9. Al ejecutar el código, se detendrá antes de que se ejecuten las instrucciones de esta línea de código.  
  
 ![Punto de interrupción de Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")  
  
 Cuando el código se interrumpe, la línea de código marcada no se ha ejecutado aún. En este momento, quizás quiera ejecutar las instrucciones de la línea de código marcada por el punto de interrupción e inspeccionar los valores cambiados. Esto se denomina "ejecutar paso a paso" el código. Si el código marcado es una llamada a método, para ejecutarlo paso a paso presione F11. También puede "saltarse" la línea de código presionando F10. Para obtener más información sobre las acciones de los puntos de interrupción, vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).  
  
 Entre los usos habituales de los puntos de interrupción se incluyen:  
  
1.  Para reducir el origen de un bloqueo, dispérselos por todo el código de la llamada a métodos que crea que está causando el error. A medida que ejecute el código paso a paso, quite y restablezca los puntos de interrupción más próximos entre sí hasta que encuentre la línea de código incorrecta.  
  
2.  Cuando introduzca código nuevo, establezca un punto de interrupción al principio del mismo y ejecute el código paso a paso para asegurarse de que se comporta tal y como se espera.  
  
3.  Si ha implementado un comportamiento complejo, establezca puntos de interrupción para el código algorítmico de modo que pueda inspeccionar los valores de las variables y los datos cuando el programa se interrumpa.  
  
4.  Si está escribiendo código de C o C++, use puntos de interrupción para detener el código y poder inspeccionar los valores de dirección (busque NULL) y los recuentos de referencias al depurar errores relacionados con la memoria.  
  
 Para obtener más información sobre el uso de puntos de interrupción, vea [Usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
### <a name="setting-conditional-breakpoints"></a>Establecer puntos de interrupción condicionales  
 Si tiene un punto de interrupción en un bucle o recursividad, o si tiene muchos puntos de interrupción que ejecuta paso a paso con frecuencia, use un punto de interrupción condicional para asegurarse de que el código se suspende únicamente cuando se cumplen determinadas condiciones. De lo contrario, se verá presionando F11 demasiadas veces.  
  
 Para establecer un punto de interrupción condicional y suspender el código cuando una variable se establezca en un determinado valor o supere un umbral determinado, haga clic en el margen para establecer un punto de interrupción y, después, seleccione el "engranaje" en el menú de desplazamiento que aparece.  
  
 ![Configuración de punto de interrupción de Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")  
  
 Verá un cuadro de diálogo con este aspecto, donde puede establecer las condiciones específicas para que se produzca la interrupción.  
  
 ![Visual Studio 2015 de punto de interrupción condicional](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")  
  
 Para obtener más detalles sobre cómo declarar las expresiones usadas para evaluar los puntos de interrupción condicionales, consulte el vídeo de Channel9 [experiencia de configuración de punto de interrupción en Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).  
  
### <a name="inspecting-your-code-at-run-time"></a>Inspeccionar el código en tiempo de ejecución  
 Cuando el código en ejecución alcanza un punto de interrupción y se detiene, puede inspeccionar las variables y las pilas de llamadas para determinar qué está sucediendo. ¿Los valores están dentro de los intervalos que esperaba? ¿Las llamadas se están realizando en el orden correcto?  
  
 ![Visual Studio 2015 ejecutar&#45;inspección del valor de tiempo](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")  
  
 Mantenga el mouse sobre una variable para ver los valores y las referencias que contiene actualmente. Si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o en las líneas de código que realizan la llamada. Suba los puntos de interrupción o agregue condiciones a los puntos de interrupción existentes para restringir aún más la búsqueda.  
  
 Además, Visual Studio 2015 muestra la ventana Herramientas de diagnóstico, donde puede observar el uso que hace la aplicación de la memoria y la CPU con el tiempo. Puede usarlas para buscar un uso intensivo de la CPU o una asignación de memoria imprevistos. Úsela con la ventana **Inspección** y con puntos de interrupción para determinar qué está causando un uso intensivo o problemas de liberación de recursos inesperados.  
  
 ![Ventana de Visual Studio 2015 Diagnostic Tools](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")  
  
### <a name="running-unit-tests"></a>Ejecutar pruebas unitarias  
 Las pruebas unitarias son programas que actúan sobre rutas de acceso a código en su aplicación o servicio. Visual Studio instala los entornos de pruebas unitarias de Microsoft tanto para código administrado como nativo. Use un entorno de pruebas unitarias para crear pruebas unitarias, ejecutarlas y notificar los resultados de las mismas. Cuando realice cambios, vuelva a ejecutar las pruebas unitarias para probar que el código sigue funcionando correctamente. Si usa Visual Studio 2015 Enterprise, puede ejecutar las pruebas automáticamente después de cada compilación.  
  
 Para empezar, lea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  
  
 Para obtener más información acerca de las pruebas unitarias en Visual Studio 2015 y cómo puede ayudarle a crear código de mejor calidad, lea [conceptos básicos de prueba unitaria](../test/unit-test-basics.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)



