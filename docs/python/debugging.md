---
title: "Depuración de Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2192dc77-b5da-4332-b753-fa20f03f81e0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: e15edc1f2739cad0960619aa6cb4b089589eebd8
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="debugging-your-python-code"></a>Depuración del código Python

Visual Studio proporciona una experiencia de depuración completa para Python, lo que incluye la asociación a procesos en ejecución, la evaluación de expresiones en las ventanas Inspección e Inmediato, la inspección de variables locales, los puntos de interrupción, las instrucciones de depuración paso a paso por instrucciones/salir de la depuración/depuración paso a paso procedimiento, la opción Establecer la instrucción siguiente y otras muchas características. 

Para acceder a una introducción sobre la depuración, consulte el vídeo de youtube.com (3 minutos y 30 segundos) [Getting Started with PTVS, Part 4: Debugging](https://youtu.be/bO7wpzgy74A?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introducción a PTVS, parte 4: depuración).

> [!VIDEO https://www.youtube.com/embed/bO7wpzgy74A]

En este tema:

- [Depuración básica](#basic-debugging)
- [Opciones de depuración de proyectos](#project-debugging-options)
- [Ventana interactiva de depuración](#the-debug-interactive-window)

Vea también los siguientes temas de depuración específicos para distintos escenarios:

- [Cross-platform remote debugging](debugging-cross-platform-remote.md) (Depuración remota multiplataforma)
- [Azure remote debugging](debugging-azure-remote.md) (Depuración remota de Azure)
- [Mixed-mode Python/C++ debugging](debugging-mixed-mode.md) (Depuración en modo mixto Python/C++)
- [Symbols for mixed-mode debugging](debugging-symbols-for-mixed-mode.md) (Símbolos de depuración en modo mixto)

<a name="debugging-without-a-project"</a>
> [!Tip]
> Python en Visual Studio admite la depuración sin un proyecto. Con un archivo independiente de Python abierto, haga clic con el botón derecho en el editor y seleccione **Start with Debugging** (Iniciar con depuración). Visual Studio lanzará el script con el entorno predeterminado global (consulte [Entornos de Python](python-environments.md) y sin argumentos. Pero desde ese momento, dispone de compatibilidad total para depuración.
>
> Para controlar el entorno y los argumentos, debe crear un proyecto para el código. Puede hacerlo fácilmente con la plantilla [From Existing Python Code](python-projects.md#creating-a-project-from-existing-files) (A partir del código Python existente).

<a name="debugging-with-a-project"</a>
## <a name="basic-debugging"></a>Depuración básica

El flujo de trabajo de depuración básica conlleva configurar puntos de interrupción, recorrer paso a paso el código, inspeccionar valores y administrar excepciones, tal y como se describe en las secciones siguientes. Para obtener información detallada sobre el depurador de Visual Studio, vea [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md) (Depuración en Visual Studio).

Puede iniciar una sesión de depuración con el comando **Depurar > Iniciar depuración**, el botón **Iniciar** de la barra de herramientas o la tecla F5. Se abrirá el archivo de inicio del proyecto (se muestra en negrita en el Explorador de soluciones) con el entorno del proyecto activo y los argumentos de línea de comandos o las rutas de búsqueda que se han especificado en las propiedades del proyecto (vea [Opciones de depuración de proyectos](#project-debugging-options)). Pero si por alguna razón no tiene un archivo de inicio configurado, verá que una ventana de salida de Python aparece brevemente y luego desaparece. En este caso, haga clic con el botón derecho en el archivo adecuado y seleccione **Establecer como archivo de inicio**.

> [!Note]
> El depurador siempre se inicia con el entorno de Python activo para el proyecto. Para cambiar de entorno, active otro distinto como se describe en [Python Environments](python-environments.md) (Entornos de Python).

### <a name="breakpoints"></a>Puntos de interrupción

Los puntos de interrupción detienen la ejecución del código en un punto especificado, a fin de poder inspeccionar el estado del programa. Para establecerlos, haga clic en el margen izquierdo del Editor de código o haga clic con el botón derecho en una línea de código y seleccione **Punto de interrupción > Insertar punto de interrupción**. En cada línea con un punto de interrupción, aparece un punto rojo.

![Puntos de interrupción en Visual Studio](~/python/media/debugging-breakpoints.png)

Para eliminar un punto de interrupción, haga clic en el punto rojo o haga clic con el botón derecho en la línea de código y seleccione **Punto de interrupción > Eliminar punto de interrupción**. También puede deshabilitarlo sin quitarlo; para ello, use el comando **Punto de interrupción > Deshabilitar punto de interrupción**.

> [!Note]
> Algunos puntos de interrupción de Python pueden resultar sorprendentes a quienes están habituados a otros lenguajes. En Python, todo el archivo es código ejecutable, por lo que Python ejecuta el archivo cuando se carga para procesar cualquier definición de clase o función de nivel superior. Si se ha establecido un punto de interrupción, puede observar que el depurador se interrumpe parcialmente a través de una declaración de clase. Este comportamiento es correcto, si bien a veces puede resultar sorprendente.

Puede personalizar las condiciones en que se desencadena un punto de interrupción, como que la interrupción se lleve a cabo cuando una variable alcanza un valor concreto. Para definir las condiciones, haga clic con el botón derecho en el punto rojo del punto de interrupción, seleccione **Condición** y después cree expresiones con código Python. Para obtener detalles sobre esta característica de Visual Studio, vea [Condiciones de punto de interrupción](../debugger/using-breakpoints.md#breakpoint-conditions).

Al definir las condiciones, también puede completar el campo **Acción** y crear un mensaje para registrarlo en la ventana de salida, con la opción de que la ejecución continúe automáticamente. Con esta operación, se crea un *punto de seguimiento* sin tener que especificar código de registro directamente en la aplicación:

![Creación de un punto de seguimiento con un punto de interrupción](~/python/media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Ejecución paso a paso del código

Una vez detenido en un punto de interrupción, hay varias maneras de recorrer el código paso a paso o de ejecutar bloques de código antes de que se produzca una nueva interrupción. Estos comandos están disponibles en varios lugares, como la barra de herramientas de depuración de la parte superior, el menú **Depurar**, en el menú contextual del Editor de código y a través de métodos abreviados de teclado (no todos los comandos están en todos los lugares):

| Característica | Pulsación de tecla | Descripción |
| --- | --- | --- |
| Continuar | F5 | Ejecuta código hasta que se alcanza el punto de interrupción siguiente. |
| Paso a paso por instrucciones | F11 | Ejecuta la instrucción siguiente y se detiene. Si la siguiente instrucción es una llamada a una función, el depurador se detiene en la primera línea de la función que se va a invocar. |
| Paso a paso por procedimientos | F10 | Ejecuta la siguiente instrucción, como realizar una llamada a una función (mediante la ejecución de todo su código) y aplicar cualquier valor devuelto. Esta acción permite omitir con facilidad aquellas funciones que no necesita depurar. |
| Paso a paso para salir | Mayús+F11 | Ejecuta el código hasta el final de la función actual y después pasa a la instrucción de llamada. Resulta útil cuando no necesita depurar el resto de la función actual. |
| Ejecutar hasta el cursor | Ctrl+F10 | Ejecuta código hasta la ubicación del operador exponencial en el editor. Permite saltar fácilmente un segmento de código que no necesita depurar. |
| Establecer instrucción siguiente | Ctrl+Mayús+F10 | Cambia el punto de ejecución actual del código a la ubicación del operador exponencial. Permite omitir por completo la ejecución de un segmento de código, por ejemplo, cuando sabe que es erróneo o que produce un efecto secundario no deseado. |
| Mostrar la instrucción siguiente | Alt+Núm * | Lo remite a la instrucción siguiente que se va a ejecutar. Resulta muy útil si ha mirado el código, pero no sabe dónde está detenido el depurador realmente. |

### <a name="inspecting-and-modifying-values"></a>Inspección y modificación de valores

Cuando el depurador se detiene, puede inspeccionar y modificar los valores de variables. También puede utilizar la ventana Inspección para supervisar las variables individuales y las expresiones personalizadas. Vea [Inspect Variables](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) (Inspección de variables) para obtener información general.

Para ver un valor con Información sobre datos, solo tiene que mover el puntero sobre cualquier variable en el editor. Puede hacer clic en el valor para cambiarlo:

![Información sobre datos del depurador](~/python/media/debugging-quick-tips.png)

La ventana Automático (**Depurar > Ventanas > Automático**) contiene las variables y expresiones que están cerca de la instrucción actual. Puede hacer doble clic en la columna de valor o seleccionar y presionar F2 para modificar el valor:

![Ventana Automático en el depurador](~/python/media/debugging-autos-window.png)

La ventana Variables locales (**Depurar > Ventanas > Variables locales**) muestra todas las variables que se encuentran en el ámbito actual, que se pueden volver a modificar:

![Ventana Variables locales en el depurador](~/python/media/debugging-locals-window.png)

Para obtener más información sobre el uso de las ventanas Automático y Variables locales, vea [Inspecting Variables in the Autos and Locals Windows](../debugger/autos-and-locals-windows.md) (Inspección de variables en las ventanas Automático y Variables locales).

Las ventanas Inspección (**Depurar > Ventanas > Inspección > Inspección 1-4**) permiten especificar expresiones arbitrarias de Python y ver los resultados. Las expresiones se vuelven a evaluar para cada paso:

![Ventana Inspección en el depurador](~/python/media/debugging-watch-window.png)

Para obtener más información sobre el uso de Inspección, vea [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../debugger/watch-and-quickwatch-windows.md) (Establecimiento de una ventana Inspección en variables que usan las ventanas Inspección e Inspección rápida en Visual Studio).

Al inspeccionar un valor de cadena (`str`, `unicode`, `bytes` y `bytearray` se consideran cadenas para este propósito), verá un icono de lupa a la derecha del valor. Al hacer clic en él, se muestra el valor de cadena sin comillas en un cuadro de diálogo emergente, con las opciones de ajuste y desplazamiento, que resultan útiles para cadenas largas. Además, al hacer clic en la flecha desplegable en el icono, puede seleccionar texto sin formato y visualizaciones HTML, XML y JSON:

![Visualizadores de cadena](~/python/media/debugging-string-visualizers.png)

Las visualizaciones HTML, XML y JSON aparecen en ventanas emergentes independientes con resaltado de sintaxis y vistas de árbol.

### <a name="exceptions"></a>Excepciones

Si se produce algún error mientras se depura el programa y no dispone de un controlador de excepciones para él, el depurador se interrumpe en el punto de la excepción:

![Cuadro emergente de excepciones](~/python/media/debugging-exception-popup.png)

En este punto puede inspeccionar el estado del programa, incluida la pila de llamadas. Sin embargo, si intenta recorrer el código, la excepción continuará produciéndose hasta que se gestione o hasta que el programa se cierre.

El comando de menú **Depurar > Ventanas > Configuración de excepciones** abre una ventana en la que puede expandir **Excepciones de Python**:

![Ventana de excepciones](~/python/media/debugging-exception-settings.png)

La casilla de cada excepción controla si el depurador *siempre* se interrumpe cuando se produce la excepción. Debe activar esta casilla si desea que las interrupciones sean más frecuentes para una excepción concreta.

De forma predeterminada, la mayoría de las excepciones activarán una interrupción cuando no se pueda encontrar un controlador de excepciones en el código fuente. Para cambiar este comportamiento, haga clic con el botón derecho en cualquier excepción y active o desactive "Continuar cuando no se controle en el código de usuario". Debe desactivar esta casilla si desea que las interrupciones sean menos frecuentes para una excepción.

Para configurar una excepción que no aparece en esta lista, haga clic en el botón **Agregar** para agregarla. El nombre debe coincidir con el nombre completo de la excepción.

## <a name="project-debugging-options"></a>Opciones de depuración de proyectos

De forma predeterminada, el depurador inicia el programa con el selector de Python estándar, sin argumentos de línea de comandos ni otras rutas de acceso o condiciones especiales. Estos pueden cambiarse mediante las propiedades de depuración del proyecto; para acceder a ellas, haga clic con el botón derecho en el Explorador de soluciones, seleccione **Propiedades** y después la pestaña **Depurar**.

![Propiedades de depuración de proyectos](~/python/media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opciones de Modo de inicio

Las opciones de **Modo de inicio** permiten elegir entre las siguientes opciones, que habilitan escenarios distintos:

| Opción | Descripción |
| --- | --- |
| Selector de Python estándar | Utiliza código de depuración escrito en Portable Python que es compatible con CPython, IronPython y variantes, como Stackless Python. Proporciona la mejor experiencia de depuración de código Python puro. Al realizar una asociación a un proceso `python.exe` en ejecución, se utiliza este selector. Este selector también proporciona [depuración en modo mixto](debugging-mixed-mode.md) para CPython, que permite cambiar sin problemas entre los códigos C/C++ y Python. |
| Selector web | Inicia el explorador predeterminado para la selección y habilita la depuración de plantillas. Vea la sección de [depuración de plantillas web](template-web.md#debugging) para obtener más información. |
| Selector web Django | Idéntico al selector web y se muestra solo para la compatibilidad con versiones anteriores. |
| Selector de IronPython (.NET) | Usa el depurador de .NET, que solo funciona con IronPython, pero permite cambiar entre cualquier proyecto en lenguaje .NET, incluidos C# y VB. Este selector se usa para establecer una asociación con un proceso .NET en ejecución que hospeda IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opciones de ejecución (rutas de búsqueda, argumentos de inicio y variables de entorno)

| Opción | Descripción |
| --- | --- |
| Rutas de búsqueda | Coinciden con lo que se muestra en el nodo Rutas de búsqueda del proyecto en el Explorador de soluciones. Puede modificar este valor aquí, pero es más fácil usar el Explorador de soluciones, ya que permite examinar carpetas y convierte automáticamente las rutas de acceso en un formato relativo. |
| Argumentos de script | Se agregan al comando utilizado para iniciar el script, y aparecen después del nombre de archivo del script. El primer elemento aquí estará disponible para el script como `sys.argv[1]`, el segundo como `sys.argv[2]`, y así sucesivamente. |
| Argumentos del intérprete | Se agregan a la línea de comandos del selector antes del nombre del script. Los argumentos comunes aquí son `-W ...` para controlar advertencias, `-O` para optimizar ligeramente el programa y `-u` para utilizar E/S no almacenada en el búfer. Los usuarios de IronPython probablemente usen este campo para pasar opciones `-X`, como `-X:Frames` o `-X:MTA`. |
| Ruta de acceso del intérprete | Reemplaza la ruta de acceso asociada con el entorno actual. Puede resultar útil para iniciar el script con un intérprete no estándar. |
| Variables de entorno | En este cuadro de texto multilínea, agregue entradas con el formato `NAME=VALUE`. Esta configuración se aplica al final, encima de cualquier variable de entorno global existente y, después, `PYTHONPATH` se establece según la configuración de Rutas de búsqueda, a fin de poder usarla para reemplazar manualmente cualquier de ellas. |

<a name="the-debug-interactive-window"</a>
## <a name="immediate-and-interactive-windows"></a>Ventana Inmediato e interactiva

Existen dos ventanas interactivas que puede utilizar durante una sesión de depuración: la ventana Inmediato de Visual Studio estándar y la ventana de depuración de Python interactiva.

La ventana Inmediato (**Depurar > Ventanas > Inmediato**) se utiliza para la evaluación rápida de expresiones de Python y la inspección o la asignación de variables en el programa en ejecución. Vea el tema general [Ventana Inmediato](../ide/reference/immediate-window.md) para obtener más información.

La ventana interactiva de depuración de Python (**Depurar > Ventanas > Depuración de Python interactiva**) está más enriquecida, ya que habilita la experiencia de [REPL interactivo](interactive-repl.md) completa durante la depuración, incluido el código de escritura y ejecución. Se conecta automáticamente a cualquier proceso iniciado en el depurador mediante el selector de Python estándar (incluidos los procesos asociados a través de **Depurar > Asociar al proceso*). No obstante, no está disponible si se usa la depuración en modo mixto de C/C++.

![Ventana Depuración de Python interactiva](~/python/media/debugging-interactive.png)

La ventana Depuración interactiva admite metacomandos especiales además de los [comandos estándar de REPL](interactive-repl.md#meta-commands):

| Comando | Argumentos | Descripción |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Inicia la ejecución del programa a partir de la instrucción actual. |
| `$down`, `$d` | Baja el marco actual un nivel en el seguimiento de la pila. |
| `$frame` | | Muestra el identificador del marco actual.
| `$frame` | Identificador del marco | Cambia el marco actual al identificador del marco especificado.
| `$load` | Carga los comandos del archivo y los ejecuta hasta que terminan. |
| `$proc` |  | Muestra el identificador de proceso actual. |
| `$proc` | Identificador de proceso | Cambia el proceso actual al identificador de proceso especificado. |
| `$procs` | | Muestra los procesos que se están depurando actualmente. |
| `$stepin`, `$step`, `$s` | Recorre paso a paso instrucciones hasta llegar a la siguiente llamada de función, si es posible. |
| `$stepout`, `$return`, `$r` | Sale paso a paso de la función actual. |
| `$stepover`, `$until`, `$unt` | Pasa por alto la siguiente llamada de función. |
| `$thread` | | Muestra el identificador de subproceso actual. |
| `$thread` | Identificador de subproceso | Cambia el subproceso actual al identificador de subproceso especificado. |
| `$threads` | | Muestra los subprocesos que se están depurando actualmente. |
| `$up`, `$u` | | Sube el marco actual un nivel en el seguimiento de la pila. |
| `$where`, `$w`, `$bt` | Muestra los marcos del subproceso actual. |

Tenga en cuenta que las ventanas del depurador estándar, como Procesos, Subprocesos y Pila de llamadas, no están sincronizadas con la ventana Depuración interactiva. Esto significa que cambiar el proceso, subproceso o marco activo en el ventana Depuración interactiva no afectará a otras ventanas del depurador y, a la inversa, cambiar el proceso, subproceso o marco activo en las otras ventanas del depurador no afectará a la ventana Depuración interactiva.

La ventana Depuración interactiva tiene su propio conjunto de opciones, a las que puede acceder en **Herramientas > Opciones > Herramientas de Python > Ventana Depuración interactiva**. A diferencia de la ventana interactiva de Python habitual, que tiene una instancia independiente para cada entorno Python, solo haya una ventana Depuración interactiva, que siempre usa el intérprete de Python para el proceso que se depura.

![Opciones de la ventana Depuración interactiva](~/python/media/debugging-interactive-options.png)
