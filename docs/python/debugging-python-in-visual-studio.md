---
title: Depuración de código de Python
description: Tutorial sobre las características de depuración de Visual Studio que son específicas del código de Python, incluido el establecimiento de puntos de interrupción, la ejecución paso a paso, la inspección de valores, el examen de excepciones y la depuración en la ventana interactiva.
ms.date: 07/13/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 14716aa85245dcbd7c1ba0bc85824f5a53bece2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079828"
---
# <a name="debug-your-python-code"></a>Depurar el código de Python

Visual Studio proporciona una experiencia de depuración completa para Python, lo que incluye la asociación a procesos en ejecución, la evaluación de expresiones en las ventanas Inspección e Inmediato, la inspección de variables locales, los puntos de interrupción, las instrucciones de depuración paso a paso por instrucciones/salir de la depuración/depuración paso a paso procedimiento, la opción Establecer la instrucción siguiente y otras muchas características.

Vea también los siguientes artículos de depuración específicos para distintos escenarios:

- [Depuración remota de Linux](debugging-python-code-on-remote-linux-machines.md)
- [Azure remote debugging](debugging-remote-python-code-on-azure.md) (Depuración remota de Azure)
- [Mixed-mode Python/C++ debugging](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) (Depuración en modo mixto Python/C++)
- [Symbols for mixed-mode debugging](debugging-symbols-for-mixed-mode-c-cpp-python.md) (Símbolos de depuración en modo mixto)

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Eche un vistazo a un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) para ver una demostración de la depuración de Python (3 minutos 32 segundos).|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python en Visual Studio admite la depuración sin un proyecto. Con un archivo independiente de Python abierto, haga clic con el botón derecho en el editor y seleccione **Iniciar con depuración**. Visual Studio inicia el script con el entorno predeterminado global (vea [Entornos de Python](managing-python-environments-in-visual-studio.md)) y sin argumentos. Pero desde ese momento, dispone de compatibilidad total para depuración.
>
> Para controlar el entorno y los argumentos, cree un proyecto para el código de manera sencilla con la plantilla de proyecto [Desde código de Python existente](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files).

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Depuración básica

El flujo de trabajo de depuración básica conlleva configurar puntos de interrupción, recorrer paso a paso el código, inspeccionar valores y administrar excepciones, tal y como se describe en las secciones siguientes.

Puede iniciar una sesión de depuración con el comando **Depurar > Iniciar depuración**, el botón **Iniciar** de la barra de herramientas o la tecla F5. Estas acciones inician el archivo de inicio del proyecto (se muestra en negrita en el Explorador de soluciones) con el entorno del proyecto activo y los argumentos de línea de comandos o las rutas de búsqueda que se han especificado en las propiedades del proyecto (vea [Opciones de depuración de proyectos](#project-debugging-options)). **Visual Studio 2017, versión 15.6** y posteriores, le avisa si no tiene un archivo de inicio configurado; en las versiones anteriores, es posible que se abra una ventana de salida con el intérprete de Python en ejecución o que la ventana de salida aparezca brevemente y luego desaparezca. En cualquier caso, haga clic con el botón derecho en el archivo adecuado y seleccione **Establecer como archivo de inicio**.

> [!Note]
> El depurador siempre se inicia con el entorno de Python activo para el proyecto. Para cambiar el entorno, active otro distinto tal como se describe en el tema sobre cómo [seleccionar un entorno de Python para un proyecto](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Puntos de interrupción

Los puntos de interrupción detienen la ejecución del código en un punto especificado, a fin de poder inspeccionar el estado del programa. Para establecer los puntos de interrupción, haga clic en el margen izquierdo del Editor de código o haga clic con el botón derecho en una línea de código y seleccione **Punto de interrupción > Insertar punto de interrupción**. En cada línea con un punto de interrupción, aparece un punto rojo.

![Puntos de interrupción en Visual Studio](media/debugging-breakpoints.png)

Para eliminar un punto de interrupción, haga clic en el punto rojo o haga clic con el botón derecho en la línea de código y seleccione **Punto de interrupción > Eliminar punto de interrupción**. También puede deshabilitarlo sin quitarlo; para ello, use el comando **Punto de interrupción > Deshabilitar punto de interrupción**.

> [!Note]
> Algunos puntos de interrupción de Python pueden resultar sorprendentes para aquellos desarrolladores que hayan trabajado con otros lenguajes de programación. En Python, todo el archivo es código ejecutable, por lo que Python ejecuta el archivo cuando se carga para procesar cualquier definición de clase o función de nivel superior. Si se ha establecido un punto de interrupción, puede observar que el depurador se interrumpe parcialmente a través de una declaración de clase. Este comportamiento es correcto, aunque a veces sea extraño.

Puede personalizar las condiciones en que se desencadena un punto de interrupción, como que la interrupción se lleve a cabo cuando una variable se establece en un valor concreto o en un intervalo de valor. Para definir las condiciones, haga clic con el botón derecho en el punto rojo del punto de interrupción, seleccione **Condición** y después cree expresiones con código Python. Para obtener detalles sobre esta característica de Visual Studio, vea [Condiciones de punto de interrupción](../debugger/using-breakpoints.md#breakpoint-conditions).

Al definir las condiciones, también puede completar el campo **Acción** y crear un mensaje para registrarlo en la ventana de salida, con la opción de que la ejecución continúe automáticamente. Al registrar el mensaje se crea lo que se denomina un *punto de seguimiento* sin agregar código de registro directamente en la aplicación:

![Creación de un punto de seguimiento con un punto de interrupción](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Ejecución paso a paso del código

Una vez detenido en un punto de interrupción, hay varias maneras de recorrer el código paso a paso o de ejecutar bloques de código antes de que se produzca una nueva interrupción. Estos comandos están disponibles en varios lugares, como la barra de herramientas de depuración de la parte superior, el menú **Depurar**, en el menú contextual del Editor de código y a través de métodos abreviados de teclado (no todos los comandos están en todos los lugares):

| Característica | Pulsación de tecla | Descripción |
| --- | --- | --- |
| Continuar | F5 | Ejecuta código hasta que se alcanza el punto de interrupción siguiente. |
| Paso a paso por instrucciones | F11 | Ejecuta la instrucción siguiente y se detiene. Si la siguiente instrucción es una llamada a una función, el depurador se detiene en la primera línea de la función que se va a invocar. |
| Paso a paso por procedimientos | F10 | Ejecuta la siguiente instrucción, como realizar una llamada a una función (mediante la ejecución de todo su código) y aplicar cualquier valor devuelto. Esta acción permite omitir con facilidad aquellas funciones que no necesita depurar. |
| Paso a paso para salir | Mayús+F11 | Ejecuta el código hasta el final de la función actual y después pasa a la instrucción de llamada.  Este comando resulta útil cuando no necesita depurar el resto de la función actual. |
| Ejecutar hasta el cursor | Ctrl+F10 | Ejecuta código hasta la ubicación del operador exponencial en el editor. Este comando le permite saltar fácilmente un segmento de código que no necesita depurar. |
| Establecer instrucción siguiente | Ctrl+Mayús+F10 | Cambia el punto de ejecución actual del código a la ubicación del operador exponencial. Este comando le permite omitir por completo la ejecución de un segmento de código, por ejemplo, cuando sabe que el código es erróneo o que produce un efecto secundario no deseado. |
| Mostrar la instrucción siguiente | Alt+Núm * | Le remite a la instrucción siguiente que se va a ejecutar. Este comando es útil si ha estado mirando el código, pero no recuerda dónde se ha detenido el depurador. |

### <a name="inspecting-and-modifying-values"></a>Inspección y modificación de valores

Cuando el depurador se detiene, puede inspeccionar y modificar los valores de variables. También puede utilizar la ventana Inspección para supervisar las variables individuales y las expresiones personalizadas. Vea [Inspect Variables](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) (Inspección de variables) para obtener información general.

Para ver un valor con Información sobre datos, solo tiene que mover el puntero sobre cualquier variable en el editor. Puede hacer clic en el valor para cambiarlo:

![Información sobre datos del depurador](media/debugging-quick-tips.png)

La ventana Automático (**Depurar > Ventanas > Automático**) contiene las variables y expresiones que están cerca de la instrucción actual. Puede hacer doble clic en la columna de valor o seleccionar y presionar F2 para modificar el valor:

![Ventana Automático en el depurador](media/debugging-autos-window.png)

La ventana Variables locales (**Depurar > Ventanas > Variables locales**) muestra todas las variables que se encuentran en el ámbito actual, que se pueden volver a modificar:

![Ventana Variables locales en el depurador](media/debugging-locals-window.png)

Para obtener más información sobre el uso de las ventanas Automático y Variables locales, vea [Inspecting Variables in the Autos and Locals Windows](../debugger/autos-and-locals-windows.md) (Inspección de variables en las ventanas Automático y Variables locales).

Las ventanas Inspección (**Depurar > Ventanas > Inspección > Inspección 1-4**) permiten especificar expresiones arbitrarias de Python y ver los resultados. Las expresiones se vuelven a evaluar para cada paso:

![Ventana Inspección en el depurador](media/debugging-watch-window.png)

Para obtener más información sobre el uso de Inspección, vea [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../debugger/watch-and-quickwatch-windows.md) (Establecimiento de una ventana Inspección en variables que usan las ventanas Inspección e Inspección rápida en Visual Studio).

Al inspeccionar un valor de cadena (`str`, `unicode`, `bytes` y `bytearray` se consideran cadenas para este propósito), aparece un icono de lupa a la derecha del valor. Al hacer clic en este icono, se muestra el valor de cadena sin comillas en un cuadro de diálogo emergente, con las opciones de ajuste y desplazamiento, que resultan útiles para cadenas largas. Además, seleccionar la flecha desplegable en el icono le permite seleccionar texto sin formato y visualizaciones HTML, XML y JSON:

![Visualizadores de cadena](media/debugging-string-visualizers.png)

Las visualizaciones HTML, XML y JSON aparecen en ventanas emergentes independientes con resaltado de sintaxis y vistas de árbol.

### <a name="exceptions"></a>Excepciones

Si se produce algún error en su programa durante la depuración, pero no dispone de un controlador de excepciones para él, el depurador se interrumpe en el punto de la excepción:

![Cuadro emergente de excepciones](media/debugging-exception-popup.png)

En este punto puede inspeccionar el estado del programa, incluida la pila de llamadas. En cambio, si intenta recorrer el código, la excepción sigue produciéndose hasta que se controle o hasta que el programa se cierre.

El comando de menú **Depurar > Ventanas > Configuración de excepciones** abre una ventana en la que puede expandir **Excepciones de Python**:

![Ventana de excepciones](media/debugging-exception-settings.png)

La casilla de cada excepción controla si el depurador *siempre* se interrumpe cuando se produce la excepción. Active esta casilla si quiere que las interrupciones sean más frecuentes para una excepción concreta.

De manera predeterminada, la mayoría de las excepciones activan una interrupción cuando no se pueda encontrar un controlador de excepciones en el código fuente. Para cambiar este comportamiento, haga clic con el botón derecho en cualquier excepción y modifique la opción **Continuar cuando no se controle en el código de usuario**. Desactive esta casilla si quiere que las interrupciones sean menos frecuentes para una excepción.

Para configurar una excepción que no aparece en esta lista, haga clic en el botón **Agregar** para agregarla. El nombre debe coincidir con el nombre completo de la excepción.

## <a name="project-debugging-options"></a>Opciones de depuración de proyectos

De forma predeterminada, el depurador inicia el programa con el selector de Python estándar, sin argumentos de línea de comandos ni otras rutas de acceso o condiciones especiales. Las opciones de inicio se cambian mediante las propiedades de depuración del proyecto; para acceder a ellas, haga clic con el botón derecho en el Explorador de soluciones, seleccione **Propiedades** y después la pestaña **Depurar**.

![Propiedades de depuración de proyectos](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opciones de Modo de inicio

| Opción | Descripción |
| --- | --- |
| Selector de Python estándar | Utiliza código de depuración escrito en Portable Python que es compatible con CPython, IronPython y variantes, como Stackless Python. Proporciona la mejor experiencia de depuración de código Python puro. Al realizar una asociación a un proceso `python.exe` en ejecución, se utiliza este selector. Este selector también proporciona [depuración en modo mixto](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) para CPython, que permite cambiar sin problemas entre los códigos C/C++ y Python. |
| Selector web | Inicia el explorador predeterminado para la selección y habilita la depuración de plantillas. Vea la sección de [depuración de plantillas web](python-web-application-project-templates.md#debugging) para obtener más información. |
| Selector web Django | Idéntico al selector web y se muestra solo para la compatibilidad con versiones anteriores. |
| Selector de IronPython (.NET) | Usa el depurador de .NET, que solo funciona con IronPython, pero permite cambiar entre cualquier proyecto en lenguaje .NET, incluidos C# y VB. Este selector se usa para establecer una asociación con un proceso .NET en ejecución que hospeda IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opciones de ejecución (rutas de búsqueda, argumentos de inicio y variables de entorno)

| Opción | Descripción |
| --- | --- |
| Rutas de búsqueda | Estos valores coinciden con lo que se muestra en el nodo Rutas de búsqueda del proyecto en el Explorador de soluciones. Puede modificar este valor aquí, pero es más fácil usar el Explorador de soluciones, ya que permite examinar carpetas y convierte automáticamente las rutas de acceso en un formato relativo. |
| Argumentos de script | Estos argumentos se agregan al comando que se ha usado para iniciar el script, y aparecen después del nombre de archivo del script. El primer elemento aquí está disponible para el script como `sys.argv[1]`, el segundo como `sys.argv[2]`, y así sucesivamente. |
| Argumentos del intérprete | Estos argumentos se agregan a la línea de comandos del iniciador antes del nombre del script. Los argumentos comunes aquí son `-W ...` para controlar advertencias, `-O` para optimizar ligeramente el programa y `-u` para utilizar E/S no almacenada en el búfer. Los usuarios de IronPython probablemente usen este campo para pasar opciones `-X`, como `-X:Frames` o `-X:MTA`. |
| Ruta de acceso del intérprete | Reemplaza la ruta de acceso asociada con el entorno actual.  el valor puede resultar útil para iniciar el script con un intérprete no estándar. |
| Variables de entorno | En este cuadro de texto multilínea, agregue entradas con el formato `NAME=VALUE`. Como esta configuración se aplica al final, encima de cualquier variable de entorno global existente y, después, `PYTHONPATH` se establece según la configuración de Rutas de búsqueda, puede usarse para reemplazar manualmente cualquier de esas otras variables. |

<a name="the-debug-interactive-window"></a>

## <a name="immediate-and-interactive-windows"></a>Ventana Inmediato e interactiva

Existen dos ventanas interactivas que puede utilizar durante una sesión de depuración: la ventana Inmediato de Visual Studio estándar y la ventana de depuración de Python interactiva.

La ventana Inmediato (**Depurar > Ventanas > Inmediato**) se utiliza para la evaluación rápida de expresiones de Python y la inspección o la asignación de variables en el programa en ejecución. Vea el artículo general [Ventana Inmediato](../ide/reference/immediate-window.md) para obtener más información.

La ventana interactiva de depuración de Python (**Depurar > Ventanas > Depuración de Python interactiva**) está más enriquecida, ya que habilita la experiencia de [REPL interactivo](python-interactive-repl-in-visual-studio.md) completa durante la depuración, incluido el código de escritura y ejecución. Se conecta automáticamente a cualquier proceso iniciado en el depurador mediante el selector de Python estándar (incluidos los procesos asociados a través de **Depurar > Asociar al proceso**). No obstante, no está disponible si se usa la depuración en modo mixto de C/C++.

![Ventana Depuración de Python interactiva](media/debugging-interactive.png)

La ventana Depuración interactiva admite metacomandos especiales además de los [comandos estándar de REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

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

Tenga en cuenta que las ventanas del depurador estándar, como Procesos, Subprocesos y Pila de llamadas, no están sincronizadas con la ventana Depuración interactiva. Cambiar el marco, subproceso o proceso activo en la ventana Depuración interactiva no afecta a las otras ventanas del depurador. De manera similar, cambiar el marco, subproceso o proceso activo en las otras ventanas del depurador no afecta a la ventana Depuración interactiva.

La ventana Depuración interactiva tiene su propio conjunto de opciones, a las que puede acceder en **Herramientas > Opciones > Herramientas de Python > Ventana Depuración interactiva**. A diferencia de la ventana interactiva de Python habitual, que tiene una instancia independiente para cada entorno Python, solo haya una ventana Depuración interactiva, que siempre usa el intérprete de Python para el proceso que se depura. Vea [Opciones: Opciones de depuración](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Opciones de la ventana Depuración interactiva](media/debugging-interactive-options.png)

## <a name="use-the-experimental-debugger"></a>Usar el depurador experimental

A partir de Visual Studio 2017 Preview 4.0, puede usar el "depurador experimental", que se basa en ptvsd versión 4.1+. Para ello, seleccione el comando de menú **Herramientas** > **Opciones** y luego vaya a **Python** > **Experimental** en el cuadro de diálogo Opciones y seleccione **Usar el depurador experimental**.

El depurador experimental solo es compatible con entornos de Python limitados, como se explica en la tabla siguiente:

| Versión de Python | Compatible con el depurador experimental |
| --- | --- |
| 2.6 | No |
| 2.7 | Sí |
| 3.1 a 3.4 | No |
| 3.5 y versiones posteriores | Sí |
| IronPython | No |

Si intenta usar el depurador experimental con un entorno no compatible, Visual Studio muestra el error, "El depurador no es compatible con este entorno":

![Error El depurador no es compatible con este entorno al usar al depurador experimental](media/debugging-experimental-incompatible-error.png)

Seleccione el comando **Deshabilitar el depurador experimental**, que borra la opción **Usar el depurador experimental**.

> [!Note]
> De momento, la advertencia no se muestra para Python 3.3 y 3.4.

Si ha instalado una versión anterior de ptvsd en el entorno actual (por ejemplo, una versión 4.0.x anterior de una versión 3.x necesaria para la depuración remota), Visual Studio muestra el error "No se pudo cargar el paquete del depurador" o la advertencia "Paquete del depurador obsoleto":

![Error No se pudo cargar el paquete del depurador al usar el depurador experimental](media/debugging-experimental-version-error.png)

![Advertencia Paquete del depurador obsoleto al usar el depurador experimental](media/debugging-experimental-version-warning.png)

Para administrar la instalación de ptvsd, use la pestaña **Paquetes** de la ventana **Entornos de Python** o los siguientes comandos de la línea de comandos:

```ps
# Uninstalling ptvsd causes VS to default to its bundled 4.1.x version.
pip uninstall ptvsd

# Upgrading ptvsd gives you the latest version, which may be newer than the bundled version.
# -pre is required to allow pre-release versions as currently required by the experimental debugger.
pip install --upgrade ptvsd -pre
```

> [!Important]
> Aunque puede omitir la advertencia en algunas versiones de ptvsd, es posible que Visual Studio no funcione correctamente.

## <a name="see-also"></a>Vea también

Para obtener información detallada sobre el depurador de Visual Studio, vea [Debugging in Visual Studio](../debugger/debugger-feature-tour.md) (Depuración en Visual Studio).
