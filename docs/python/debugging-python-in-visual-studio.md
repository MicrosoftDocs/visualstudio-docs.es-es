---
title: Depuración de código de Python
description: Visual Studio proporciona depuración enriquecida para código de Python, incluido el establecimiento de puntos de interrupción, la ejecución paso a paso, la inspección de valores, el examen de excepciones y la depuración en la ventana interactiva.
ms.date: 05/12/2020
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 293e431fb00f6817fdbba19186613345cb90275a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285652"
---
# <a name="debug-your-python-code"></a>Depurar el código de Python

Visual Studio proporciona una experiencia de depuración completa para Python, lo que incluye la asociación a procesos en ejecución, la evaluación de expresiones en las ventanas **Inspección** e **Inmediato**, la inspección de variables locales, los puntos de interrupción, las instrucciones Depurar paso a paso por instrucciones/procedimientos/para salir, **Establecer instrucción siguiente**, etc.

Vea también los siguientes artículos de depuración específicos para distintos escenarios:

- [Depuración remota de Linux](debugging-python-code-on-remote-linux-machines.md)
- [Mixed-mode Python/C++ debugging](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) (Depuración en modo mixto Python/C++)
- [Symbols for mixed-mode debugging](debugging-symbols-for-mixed-mode-c-cpp-python.md) (Símbolos de depuración en modo mixto)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python en Visual Studio admite la depuración sin un proyecto. Con un archivo independiente de Python abierto, haga clic con el botón derecho en el editor y seleccione **Iniciar con depuración**. Visual Studio inicia el script con el entorno predeterminado global (vea [Entornos de Python](managing-python-environments-in-visual-studio.md)) y sin argumentos. Pero desde ese momento, dispone de compatibilidad total para depuración.
>
> Para controlar el entorno y los argumentos, cree un proyecto para el código de manera sencilla con la plantilla de proyecto [Desde código de Python existente](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files).

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Depuración básica

El flujo de trabajo de depuración básica conlleva configurar puntos de interrupción, recorrer paso a paso el código, inspeccionar valores y administrar excepciones, tal y como se describe en las secciones siguientes.

Puede iniciar una sesión de depuración con el comando **Depurar** > **Iniciar depuración**, el botón **Iniciar** de la barra de herramientas o la tecla **F5**. Estas acciones inician el archivo de inicio del proyecto (se muestra en negrita en el **Explorador de soluciones**) con el entorno activo del proyecto y los argumentos de línea de comandos o las rutas de búsqueda que se hayan especificado en **Propiedades del proyecto** (vea [Project debugging options](#project-debugging-options) [Opciones de depuración de proyectos]). Visual Studio 2017, versión 15.6 y posteriores, le avisa si no tiene un archivo de inicio configurado; en las versiones anteriores, es posible que se abra una ventana de salida con el intérprete de Python en ejecución o que la ventana de salida aparezca brevemente y luego desaparezca. En cualquier caso, haga clic con el botón derecho en el archivo adecuado y seleccione **Establecer como archivo de inicio**.

> [!Note]
> El depurador siempre se inicia con el entorno de Python activo para el proyecto. Para cambiar el entorno, active otro distinto como se explica en [Cómo asignar el entorno de Python que se usa en un proyecto](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Puntos de interrupción

Los puntos de interrupción detienen la ejecución del código en un punto especificado, a fin de poder inspeccionar el estado del programa. Para establecer los puntos de interrupción, haga clic en el margen izquierdo del editor de código o haga clic con el botón derecho en una línea de código y seleccione **Punto de interrupción** > **Insertar punto de interrupción**. En cada línea con un punto de interrupción, aparece un punto rojo.

![Puntos de interrupción en Visual Studio](media/debugging-breakpoints.png)

Para eliminar un punto de interrupción, haga clic en el punto rojo o haga clic con el botón derecho en la línea de código y seleccione **Punto de interrupción** > **Eliminar punto de interrupción**. También puede deshabilitarlo sin quitarlo; para ello, use el comando **Punto de interrupción** > **Deshabilitar punto de interrupción**.

> [!Note]
> Algunos puntos de interrupción de Python pueden resultar sorprendentes para aquellos desarrolladores que hayan trabajado con otros lenguajes de programación. En Python, todo el archivo es código ejecutable, por lo que Python ejecuta el archivo cuando se carga para procesar cualquier definición de clase o función de nivel superior. Si se ha establecido un punto de interrupción, puede observar que el depurador se interrumpe parcialmente a través de una declaración de clase. Este comportamiento es correcto, aunque a veces sea sorprendente.

Puede personalizar las condiciones en que se desencadena un punto de interrupción, como que la interrupción se lleve a cabo cuando una variable se establece en un valor concreto o en un intervalo de valor. Para definir las condiciones, haga clic con el botón derecho en el punto rojo del punto de interrupción, seleccione **Condición** y después cree expresiones con código Python. Para obtener todos los detalles sobre esta característica de Visual Studio, vea [Breakpoint conditions](../debugger/using-breakpoints.md#breakpoint-conditions) (Condiciones de los puntos de interrupción).

Al definir las condiciones, también puede completar el campo **Acción** y crear un mensaje para registrarlo en la ventana de salida, con la opción de que la ejecución continúe automáticamente. Al registrar el mensaje se crea lo que se denomina un *punto de seguimiento* sin agregar código de registro directamente en la aplicación:

![Creación de un punto de seguimiento con un punto de interrupción](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Examinar el código

Una vez detenido en un punto de interrupción, hay varias maneras de recorrer el código paso a paso o de ejecutar bloques de código antes de que se produzca una nueva interrupción. Estos comandos están disponibles en varias ubicaciones, como la barra de herramientas de depuración de la parte superior, el menú **Depurar**, en el menú contextual del editor de código y mediante métodos abreviados de teclado (aunque no todos los comandos están en todas las ubicaciones):

| Característica | Pulsación de tecla | Descripción |
| --- | --- | --- |
| **Continue** | **F5** | Ejecuta código hasta que se alcanza el punto de interrupción siguiente. |
| **Depurar paso a paso por instrucciones** | **F11** | Ejecuta la instrucción siguiente y se detiene. Si la siguiente instrucción es una llamada a una función, el depurador se detiene en la primera línea de la función que se va a invocar. |
| **Paso a paso por procedimientos** | **F10** | Ejecuta la siguiente instrucción, como realizar una llamada a una función (mediante la ejecución de todo su código) y aplicar cualquier valor devuelto. Esta acción permite omitir con facilidad aquellas funciones que no necesita depurar. |
| **Paso a paso para salir** | **Mayús**+**F11** | Ejecuta el código hasta el final de la función actual y después pasa a la instrucción de llamada.  Este comando resulta útil cuando no necesita depurar el resto de la función actual. |
| **Ejecutar hasta el cursor** | **Ctrl**+**F10** | Ejecuta código hasta la ubicación del operador exponencial en el editor. Este comando le permite saltar fácilmente un segmento de código que no necesita depurar. |
| **Establecer instrucción siguiente** | **Ctrl**+**Mayús**+**F10** | Cambia el punto de ejecución actual del código a la ubicación del operador exponencial. Este comando le permite omitir por completo la ejecución de un segmento de código, por ejemplo, cuando sabe que el código es erróneo o que produce un efecto secundario no deseado. |
| **Mostrar la instrucción siguiente** | **Alt**+**Num** **&#42;**| Le remite a la instrucción siguiente que se va a ejecutar. Este comando es útil si ha estado mirando el código, pero no recuerda dónde se ha detenido el depurador. |

### <a name="inspect-and-modify-values"></a>Inspeccionar y modificar valores

Cuando el depurador se detiene, puede inspeccionar y modificar los valores de variables. También puede usar la ventana **Inspección** para supervisar variables individuales y expresiones personalizadas. (Vea [Inspeccionar variables](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) para obtener detalles).

Para ver un valor con **Información sobre datos**, solo tiene que mantener el puntero sobre cualquier variable en el editor. Puede hacer clic en el valor para cambiarlo:

![Información sobre datos en el depurador de Visual Studio](media/debugging-quick-tips.png)

La ventana **Automático** (**Depurar** > **Ventanas** > **Automático**) contiene variables y expresiones cercanas a la instrucción actual. Puede hacer doble clic en la columna de valor o seleccionar y presionar **F2** para modificar el valor:

![Ventana Automático en el depurador de Visual Studio](media/debugging-autos-window.png)

La ventana **Variables locales** (**Depurar** > **Ventanas** > **Variables locales**) muestra todas las variables que se encuentran en el ámbito actual, que se pueden volver a modificar:

![Ventana Variables locales en el depurador de Visual Studio](media/debugging-locals-window.png)

Para obtener más información sobre el uso de **Automático** y **Variables locales**, vea [Inspect variables in the Autos and Locals windows](../debugger/autos-and-locals-windows.md) (Inspeccionar las variables en las ventanas Variables locales y Automático).

Las ventanas **Inspección** (**Depurar** > **Ventanas** > **Inspección** > **Inspección 1-4**) permiten especificar expresiones arbitrarias de Python y ver los resultados. Las expresiones se vuelven a evaluar para cada paso:

![Ventana Inspección en el depurador de Visual Studio](media/debugging-watch-window.png)

Para obtener más información sobre el uso de **Inspección**, vea [Set a watch on variables using the Watch and QuickWatch windows](../debugger/watch-and-quickwatch-windows.md) (Establecimiento de una inspección en variables mediante las ventanas Inspección e Inspección rápida).

Al inspeccionar un valor de cadena (`str`, `unicode`, `bytes` y `bytearray` se consideran cadenas para este propósito), aparece un icono de lupa a la derecha del valor. Al hacer clic en este icono, se muestra el valor de cadena sin comillas en un cuadro de diálogo emergente, con las opciones de ajuste y desplazamiento, que resultan útiles para cadenas largas. Además, seleccionar la flecha desplegable en el icono le permite seleccionar texto sin formato y visualizaciones HTML, XML y JSON:

![Visualizadores de cadena en el depurador de Visual Studio](media/debugging-string-visualizers.png)

Las visualizaciones HTML, XML y JSON aparecen en ventanas emergentes independientes con resaltado de sintaxis y vistas de árbol.

### <a name="exceptions"></a>Excepciones

Si se produce algún error en su programa durante la depuración, pero no dispone de un controlador de excepciones para él, el depurador se interrumpe en el punto de la excepción:

![Ventana emergente Excepción en el depurador de Visual Studio](media/debugging-exception-popup.png)

En este punto puede inspeccionar el estado del programa, incluida la pila de llamadas. En cambio, si intenta recorrer el código, la excepción sigue produciéndose hasta que se controle o hasta que el programa se cierre.

El comando de menú **Depurar** > **Ventanas** > **Configuración de excepciones** abre una ventana en la que puede expandir **Excepciones de Python**:

![Ventana Excepciones en el depurador de Visual Studio](media/debugging-exception-settings.png)

La casilla de cada excepción controla si el depurador *siempre* se interrumpe cuando se produce la excepción. Active esta casilla si quiere que las interrupciones sean más frecuentes para una excepción concreta.

De manera predeterminada, la mayoría de las excepciones activan una interrupción cuando no se pueda encontrar un controlador de excepciones en el código fuente. Para cambiar este comportamiento, haga clic con el botón derecho en cualquier excepción y modifique la opción **Continuar cuando no se controle en el código de usuario**. Desactive esta casilla si quiere que las interrupciones sean menos frecuentes para una excepción.

Para configurar una excepción que no aparece en esta lista, haga clic en el botón **Agregar** para agregarla. El nombre debe coincidir con el nombre completo de la excepción.

## <a name="project-debugging-options"></a>Opciones de depuración de proyectos

De forma predeterminada, el depurador inicia el programa con el selector de Python estándar, sin argumentos de línea de comandos ni otras rutas de acceso o condiciones especiales. Las opciones de inicio se cambian mediante las propiedades de depuración del proyecto; para acceder a ellas, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones**, seleccione **Propiedades** y después la pestaña **Depurar**.

![Propiedades de depuración del proyecto en el depurador de Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opciones de Modo de inicio

| Opción | Descripción |
| --- | --- |
| **Iniciador de Python estándar** | Utiliza código de depuración escrito en Portable Python que es compatible con CPython, IronPython y variantes, como Stackless Python. Proporciona la mejor experiencia de depuración de código Python puro. Al realizar una asociación a un proceso *python.exe* en ejecución, se usa este iniciador. Este selector también proporciona [depuración en modo mixto](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) para CPython, que permite cambiar sin problemas entre los códigos C/C++ y Python. |
| **Iniciador web** | Inicia el explorador predeterminado para la selección y habilita la depuración de plantillas. Vea la sección de [depuración de plantillas web](python-web-application-project-templates.md#debugging) para obtener más información. |
| **Iniciador web de Django** | Idéntico al selector web y se muestra solo para la compatibilidad con versiones anteriores. |
| **Iniciador de IronPython (.NET)** | Usa el depurador de .NET, que solo funciona con IronPython, pero permite cambiar entre cualquier proyecto en lenguaje .NET, incluidos C# y VB. Este selector se usa para establecer una asociación con un proceso .NET en ejecución que hospeda IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opciones de ejecución (rutas de búsqueda, argumentos de inicio y variables de entorno)

| Opción | Descripción |
| --- | --- |
| **Rutas de búsqueda** | Estos valores coinciden con lo que se muestra en el nodo **Rutas de búsqueda** del proyecto en el **Explorador de soluciones**. Puede modificar este valor aquí, pero es más fácil usar el **Explorador de soluciones**, ya que permite examinar las carpetas y convierte automáticamente las rutas de acceso a un formato relativo. |
| **Argumentos de script** | Estos argumentos se agregan al comando que se ha usado para iniciar el script, y aparecen después del nombre de archivo del script. El primer elemento aquí está disponible para el script como `sys.argv[1]`, el segundo como `sys.argv[2]`, y así sucesivamente. |
| **Argumentos del intérprete** | Estos argumentos se agregan a la línea de comandos del iniciador antes del nombre del script. Los argumentos comunes aquí son `-W ...` para controlar advertencias, `-O` para optimizar ligeramente el programa y `-u` para utilizar E/S no almacenada en el búfer. Los usuarios de IronPython probablemente usen este campo para pasar opciones `-X`, como `-X:Frames` o `-X:MTA`. |
| **Ruta del intérprete** | Reemplaza la ruta de acceso asociada con el entorno actual. El valor puede resultar útil para iniciar el script con un intérprete no estándar. |
| **Variables de entorno** | En este cuadro de texto multilínea, agregue entradas con el formato \<NAME>=\<VALUE>. Como esta opción se aplica al final, por encima de cualquier variable de entorno global existente y, después, `PYTHONPATH` se establece según la configuración de **Rutas de búsqueda**, puede usarse para reemplazar manualmente cualquiera de esas otras variables. |

## <a name="immediate-and-interactive-windows"></a>Ventanas inmediatas e interactivas

Existen dos ventanas interactivas que puede usar durante una sesión de depuración: la ventana **Inmediato** estándar de Visual Studio y la ventana **Interactiva de depuración de Python**.

La ventana **Inmediato** (**Depurar** > **Ventanas** > **Inmediato**) se usa para la evaluación rápida de expresiones de Python y la inspección o la asignación de variables en el programa en ejecución. Vea el artículo general [Ventana Inmediato](../ide/reference/immediate-window.md) para obtener detalles.

La ventana **Interactiva de depuración de Python** (**Depurar** > **Ventanas** > **Interactiva de depuración de Python**) tiene más características, ya que habilita la experiencia completa de [REPL interactivo](python-interactive-repl-in-visual-studio.md) durante la depuración, incluidas la escritura y la ejecución de código. Se conecta automáticamente a cualquier proceso iniciado en el depurador mediante el iniciador de Python estándar (incluidos los procesos asociados mediante **Depurar** > **Asociar al proceso**). No obstante, no está disponible si se usa la depuración en modo mixto de C/C++.

![Ventana Depuración de Python interactiva](media/debugging-interactive.png)

La ventana **Interactiva de depuración** admite metacomandos especiales además de los [comandos estándar de REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Comando | Argumentos | Descripción |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Inicia la ejecución del programa a partir de la instrucción actual. |
| `$down`, `$d` | Baja el marco actual un nivel en el seguimiento de la pila. |
| `$frame` | | Muestra el identificador del marco actual.
| `$frame` | frame ID | Cambia el marco actual al identificador del marco especificado.
| `$load` | Carga los comandos del archivo y los ejecuta hasta que terminan. |
| `$proc` |  | Muestra el identificador de proceso actual. |
| `$proc` | process ID | Cambia el proceso actual al identificador de proceso especificado. |
| `$procs` | | Muestra los procesos que se están depurando actualmente. |
| `$stepin`, `$step`, `$s` | Recorre paso a paso instrucciones hasta llegar a la siguiente llamada de función, si es posible. |
| `$stepout`, `$return`, `$r` | Sale paso a paso de la función actual. |
| `$stepover`, `$until`, `$unt` | Pasa por alto la siguiente llamada de función. |
| `$thread` | | Muestra el identificador de subproceso actual. |
| `$thread` | thread ID | Cambia el subproceso actual al identificador de subproceso especificado. |
| `$threads` | | Muestra los subprocesos que se están depurando actualmente. |
| `$up`, `$u` | | Sube el marco actual un nivel en el seguimiento de la pila. |
| `$where`, `$w`, `$bt` | Muestra los marcos del subproceso actual. |

Tenga en cuenta que las ventanas estándar del depurador, como **Procesos**, **Subprocesos** y **Pila de llamadas**, no están sincronizadas con la ventana **Interactiva de depuración**. El cambio del marco, subproceso o proceso activo en la ventana **Interactiva de depuración** no afecta a las otras ventanas del depurador. Del mismo modo, el cambio del marco, subproceso o proceso activo en las otras ventanas del depurador no afecta a la ventana **Interactiva de depuración**.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Usar el depurador heredado

Visual Studio 2017 15.8 y versiones posteriores usan un depurador basado en ptvsd 4.1+. Visual Studio 2019 16.5 y las versiones posteriores usan un depurador basado en debugpy. Estas versiones del depurador son compatibles con Python 2.7 y Python 3.5+. Si usa Python 2.6, 3.1 hasta 3.4 o IronPython, Visual Studio muestra el error **El depurador no admite este entorno de Python**:

![Error "El depurador no admite este entorno de Python" cuando se usa el depurador](media/debugging-experimental-incompatible-error.png)

En estos casos, debe usar el depurador antiguo (que es el valor predeterminado en Visual Studio 2017 15.7 y versiones anteriores). Seleccione el comando del menú **Herramientas** > **Opciones**, navegue a **Python** > **Depuración** y seleccione la opción **Usar el depurador heredado**.

Si ha instalado una versión anterior de ptvsd en el entorno actual (por ejemplo, una versión 4.0.x anterior de una versión 3.x necesaria para la depuración remota), es posible que Visual Studio muestre un error o una advertencia.

El error **No se pudo cargar el paquete de depurador** aparece cuando se ha instalado ptvsd 3.x:

![Error No se pudo cargar el paquete del depurador al usar el depurador](media/debugging-experimental-version-error.png)

En este caso, seleccione **Usar el depurador heredado** para establecer la opción **Usar el depurador heredado** y reiniciar el depurador.

La advertencia **El paquete del depurador está obsoleto** aparece cuando se ha instalado una versión anterior a 4.x de ptvsd:

![Advertencia Paquete del depurador obsoleto al usar el depurador](media/debugging-experimental-version-warning.png)

> [!Important]
> Aunque puede omitir la advertencia en algunas versiones de ptvsd, es posible que Visual Studio no funcione correctamente.

Para administrar la instalación de ptvsd:

1. Navegue a la pestaña **Paquetes** en la ventana **Entornos de Python**.

1. Escriba "ptvsd" en el cuadro de búsqueda y examine la versión de ptvsd instalada:

    ![Comprobación de la versión de ptvsd en la ventana Entornos de Python](media/debugging-experimental-check-ptvsd.png)

1. Si la versión es anterior a 4.1.1a9 (la versión incluida con Visual Studio), seleccione el símbolo **X** a la derecha del paquete para desinstalar la versión anterior. Visual Studio usará la versión incluida. (También puede desinstalarla desde PowerShell mediante `pip uninstall ptvsd`).

1. Como alternativa, puede actualizar el paquete de ptvsd a su versión más reciente siguiendo las instrucciones de la sección [Solución de problemas](#troubleshooting).

## <a name="troubleshooting"></a>Solución de problemas

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>Para la actualización de ptvsd de Visual Studio 2019 (versión 16.4 y posteriores)
Si tiene problemas con el depurador, primero actualice su versión del depurador de la siguiente manera:

1. Navegue a la pestaña **Paquetes** en la ventana **Entornos de Python**.

1. Escriba `ptvsd --upgrade` en el cuadro de búsqueda y seleccione **Ejecutar comando: pip install ptvsd --upgrade**. (También puede usar el mismo comando desde PowerShell).

    ![Dar el comando de actualización de ptvsd en la ventana Entornos de Python](media/debugging-experimental-upgrade-ptvsd.png)

   Si los problemas persisten, registre un problema en el [repositorio de GitHub de PTVS](https://github.com/Microsoft/ptvs/issues).

   > [!NOTE]
   > Para Visual Studio 2019 16.5 y versiones posteriores, debugpy forma parte de la carga de trabajo de Python de Visual Studio y se actualiza junto con Visual Studio.

### <a name="enable-debugger-logging"></a>Habilitación del registro del depurador

En el transcurso de la investigación de un problema del depurador, Microsoft puede pedirle que habilite y recopile registros de depurador que ayudan en el diagnóstico.

Los pasos siguientes habilitan la depuración en la sesión actual de Visual Studio:

1. Abra una ventana de comandos en Visual Studio mediante el comando de menú **Ver** > **Otras ventanas** > **Ventana Comandos**.

1. Escriba el comando siguiente:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Inicie la depuración y recorra los pasos que sean necesarios para reproducir el problema. Durante este tiempo, los registros de depuración aparecen en la ventana **Salida** bajo **Registro del host de adaptador de depuración**. Luego puede copiar los registros de esa ventana y pegarlos en un problema de GitHub, correo electrónico, etc.

    ![Salida de registro del depurador en la ventana Salida](media/debugger-logging-output.png)

1. Si Visual Studio se bloquea o usted no es capaz de acceder a la ventana **Salida**, reinicie Visual Studio, abra una ventana de comandos y escriba el siguiente comando:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Inicie la depuración y reproduzca el problema de nuevo. Después, puede encontrar los registros del depurador en `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Vea también

Para obtener información detallada sobre el depurador de Visual Studio, vea [Debugging in Visual Studio](../debugger/debugger-feature-tour.md) (Depuración en Visual Studio).
