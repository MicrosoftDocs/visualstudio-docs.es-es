---
title: Uso de puntos de interrupción en el depurador | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2020
ms.topic: how-to
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57b2ea6a0c69387043057bc07957a757ed351f99
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769406"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Uso de puntos de interrupción en el depurador de Visual Studio

Los puntos de interrupción constituyen una de las técnicas de depuración más importantes en los cuadros de herramientas de los desarrolladores. Los puntos de interrupción se establecen donde se quiere pausar la ejecución del depurador. Por ejemplo, puede que quiera ver el estado de las variables de código o echar un vistazo a la pila de llamadas de un punto de interrupción determinado.  Si está intentando resolver una advertencia o un problema mientras usa puntos de interrupción, vea [Solución de problemas de puntos de interrupción en el depurador de Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Si conoce la tarea o el problema que está intentando resolver, pero necesita saber qué tipo de punto de interrupción usar, vea [Búsqueda de la tarea de depuración](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Establecer puntos de interrupción en el código fuente

Los puntos de interrupción pueden establecerse en cualquier línea de código ejecutable. Por ejemplo, en el siguiente código de C#, puede establecer un punto de interrupción en la línea de código con la asignación de variables (`int testInt = 1`), el bucle `for` o cualquier código dentro del bucle `for`. No se puede establecer un punto de interrupción en las firmas de método, las declaraciones de un espacio de nombres o una clase, o bien las declaraciones de variables si no hay ninguna asignación y no hay ningún captador o establecedor.

Para establecer un punto de interrupción en el código fuente, haga clic en el margen más a la izquierda junto a una línea de código. También puede seleccionar la línea y presionar **F9** y seleccionar **Depurar** > **Alternar punto de interrupción**, o hacer clic con el botón derecho y seleccionar **Punto de interrupción** > **Insertar punto de interrupción**. El punto de interrupción aparece como un punto rojo en el margen izquierdo.

En la mayoría de los lenguajes (C# incluido), las líneas de punto de interrupción y las líneas de ejecución actuales se resaltan automáticamente. En el código de C++, el resaltado de líneas de punto de interrupción y líneas de ejecución actuales se puede activar seleccionando **Herramientas** (o **Depurar**) > **Opciones** > **Depuración** >  **Resaltar en toda la línea de código fuente los puntos de interrupción y la instrucción actual (solo C++)** .

![Establecer un punto de interrupción](../debugger/media/basicbreakpoint.png "Punto de interrupción básico")

Al depurar, la ejecución se detiene en el punto de interrupción, antes de que el código de esa línea se ejecute. El símbolo de punto de interrupción muestra una flecha amarilla.

En el punto de interrupción del siguiente ejemplo, el valor de `testInt` sigue siendo 1, por lo que el valor no ha cambiado desde que la variable se inicializó (se estableció en un valor de 1), ya que la instrucción en amarillo aún no se ha ejecutado.

![Ejecución de punto de interrupción detenida](../debugger/media/breakpointexecution.png "Ejecución de un punto de interrupción")

Cuando el depurador se detiene en el punto de interrupción, se puede consultar el estado actual de la aplicación, incluidos los [valores de variable ](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) y la [pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

Estas son algunas instrucciones generales para trabajar con los puntos de interrupción.

- El punto de interrupción es un comando de alternancia. Puede hacer clic en él, presionar **F9**, o bien usar **Depurar** > **Alternar punto de interrupción** para eliminarlo o volver a insertarlo.

- Para deshabilitar un punto de interrupción sin eliminarlo, mantenga el ratón sobre él o haga clic con el botón derecho y seleccione **Deshabilitar punto de interrupción**. Los puntos de interrupción deshabilitados aparecen como puntos vacíos en el margen izquierdo o en la ventana **Puntos de interrupción**. Para volver a habilitar un punto de interrupción, mantenga el ratón sobre él o haga clic con el botón derecho y seleccione **Habilitar punto de interrupción**.

- Establezca condiciones y acciones, agregue y edite etiquetas o exporte un punto de interrupción haciendo clic con el botón derecho en él y seleccionando el comando adecuado, o bien manteniendo el ratón en él y seleccionando el icono **Configuración**.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Acciones de punto de interrupción y puntos de seguimiento

Un *punto de seguimiento* es un punto de interrupción que imprime un mensaje en la ventana **Salida**. Los puntos de seguimiento pueden actuar como una instrucción de seguimiento temporal en el lenguaje de programación, y no pausan la ejecución del código. Para crear un punto de seguimiento, establezca una acción especial en la ventana **Configuración del punto de interrupción**. Para obtener instrucciones detalladas, vea [Uso de puntos de seguimiento en el depurador de Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Condiciones de punto de interrupción

La definición de condiciones le permite controlar cuándo y dónde se ejecuta un punto de interrupción. La condición puede ser cualquier expresión válida que el depurador reconozca. Para más información sobre las expresiones válidas, vea [Expresiones en el depurador de Visual Studio](../debugger/expressions-in-the-debugger.md).

**Para establecer una condición de punto de interrupción:**

1. Haga clic con el botón derecho en el símbolo del punto de interrupción y seleccione **Condiciones**. También puede mantener el ratón sobre el símbolo del punto de interrupción, seleccionar el icono **Configuración** y, después, seleccionar **Condiciones** en la ventana **Configuración del punto de interrupción**.

   Las condiciones también se pueden establecer en la ventana **Puntos de interrupción**; para ello, haga clic con el botón derecho en un punto de interrupción, seleccione **Configuración** y, tras ello, seleccione **Condiciones**.

   ![Configuración del punto de interrupción](../debugger/media/breakpointsettings.png "Configuración del punto de interrupción")

2. En la lista desplegable, seleccione **Expresión condicional**, **Recuento de visitas** o **Filtro** y establezca el valor correspondiente.

3. Seleccione **Cerrar** o presione **Ctrl**+**Entrar** para cerrar la ventana **Configuración del punto de interrupción** (o, en la ventana **Puntos de interrupción**, seleccione **Aceptar** para cerrar el cuadro de diálogo).

Los puntos de interrupción con condiciones establecidas aparecen con un símbolo **+** en el código fuente y en las ventanas **Puntos de interrupción**.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Crear una expresión condicional

Al seleccionar **Expresión condicional**, puede elegir entre dos condiciones: **Es true** o **Cuando cambie**. Elija **Es true** para interrumpir cuando la expresión se cumpla o **Cuando cambie** para interrumpir cuando el valor de la expresión cambie.

En el siguiente ejemplo, el punto de interrupción se visita únicamente cuando el valor de `testInt` es **4**:

![Condición "Es true" del punto de interrupción](../debugger/media/breakpointconditionistrue.png "Condición "Es true" del punto de interrupción")

En el siguiente ejemplo, el punto de interrupción se visita únicamente cuando el valor de `testInt` cambia:

![Condición "Cuando cambie" del punto de interrupción](../debugger/media/breakpointwhenchanged.png "Condición "Cuando cambie" del punto de interrupción")

Si se establece una condición de punto de interrupción con una sintaxis no válida, aparecerá un mensaje de advertencia. Si se especifica una condición de punto de interrupción con una sintaxis válida pero una semántica no válida, aparecerá un mensaje de advertencia la primera vez que se visite el punto de interrupción. En ambos casos, el depurador se detendrá cuando se alcance el punto de interrupción no válido. El punto de interrupción se omitirá únicamente si la condición es válida y se evalúa como `false`.

>[!NOTE]
>El comportamiento del campo **Cuando cambie** es diferente según el lenguaje de programación.
>- El depurador no considerará la primera evaluación de la condición como cambio, por lo que no se visita el punto de interrupción en la primera evaluación.
>- En el código administrado, el depurador visita el punto de interrupción en la primera evaluación, después de seleccionar **Cuando cambie**.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Uso de identificadores de objeto en las expresiones condicionales (solo C# y F#)

 Hay ocasiones en las que se quiere observar el comportamiento de un objeto concreto. Por ejemplo, podríamos querer averiguar por qué un objeto se ha insertado en una colección más de una vez. En C# y F#, puede crear identificadores de objeto para instancias específicas de [tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types) y usarlos en condiciones de punto de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.

**Para crear un identificador de objeto:**

1. Establezca un punto de interrupción en alguna parte del código después de que se haya creado el objeto.

2. Inicie la depuración y, cuando la ejecución se detenga en el punto de interrupción, seleccione **Depurar** > **Ventanas** > **Variables locales** o **Alt**+**4** para abrir la ventana **Variables locales**.

   Busque la instancia de objeto específica en la ventana **Variables locales**, haga clic con el botón derecho en ella y seleccione **Crear el identificador del objeto**.

   Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Este es el identificador del objeto.

3. Agregue un nuevo punto de interrupción en el punto que quiera investigar (por ejemplo, cuando se agregue el objeto a la colección). Haga clic con el botón derecho en el punto de interrupción y seleccione **Condiciones**.

4. Use el identificador de objeto en el campo **Expresión condicional**. Por ejemplo, si la variable `item` es el objeto que se va a agregar a la colección, seleccione **Es true** y escriba **item == $\<n>** , donde \<n> es el número de identificación del objeto.

   La ejecución se interrumpirá en el punto cuando ese objeto se agregue a la colección.

   Para eliminar el identificador de objeto, haga clic con el botón derecho en la variable en la ventana **Locales** y seleccione **Eliminar el identificador del objeto**.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles y no impiden que el objeto se recopile en la recolección de elementos no utilizados. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

### <a name="set-a-hit-count-condition"></a>Establecer una condición de número de llamadas

Si sospecha que un bucle del código inicia un comportamiento erróneo después de cierto número de iteraciones, puede establecer un punto de interrupción que detenga la ejecución después de que se llegue a ese número de llamadas, en lugar de tener que presionar repetidamente **F5** para alcanzar esa iteración.

En la sección **Condiciones** de la ventana **Configuración del punto de interrupción**, seleccione **Número de llamadas** y, después, especifique el número de iteraciones. En el siguiente ejemplo, el punto de interrupción está configurado para alcanzarse cada dos iteraciones:

![Número de puntos de interrupción alcanzados](../debugger/media/breakpointhitcount.png "Número de llamadas del punto de interrupción")

### <a name="set-a-filter-condition"></a>Establecer una condición de filtro

Puede restringir un punto de interrupción para que se active solo en los dispositivos especificados, o bien en los procesos y subprocesos especificados.

En la sección **Condiciones** de la ventana **Configuración del punto de interrupción**, seleccione **Filtro** y, después, escriba una o varias de las siguientes expresiones:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Incluya los valores de cadena entre comillas dobles. Puede combinar las cláusulas con `&` (AND), `||` (OR), `!` (NOT) y paréntesis.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Establecer puntos de interrupción de función

La ejecución se puede interrumpir cuando se llame a una función. Esto resulta útil, por ejemplo, cuando se conoce el nombre de la función, pero no su ubicación. También es práctico si existen funciones con el mismo nombre y quiere interrumpirlas todas (por ejemplo, funciones sobrecargadas o funciones en proyectos distintos).

**Para establecer un punto de interrupción de función:**

1. Seleccione **Depurar** > **Nuevo punto de interrupción** > **Punto de interrupción de función** o presione **Alt**+**F9** > **Ctrl**+**B**.

   También puede seleccionar **Nuevo** > **Punto de interrupción de función** en la ventana **Puntos de interrupción**.

1. En el cuadro de diálogo **Nuevo punto de interrupción de función**, escriba el nombre de la función en el cuadro **Nombre de función**.

   Para restringir la especificación de la función:

   - Use el nombre completo de la función.

     Ejemplo:  `Namespace1.ClassX.MethodA()`

   - Agregue los tipos de parámetro de una función sobrecargada.

     Ejemplo:  `MethodA(int, string)`

   - Use el símbolo "!" para especificar el módulo.

     Ejemplo: `App1.dll!MethodA`

   - Use el operador de contexto en C++ nativo.

     `{function, , [module]} [+<line offset from start of method>]`

     Ejemplo: `{MethodA, , App1.dll}+2`

1. En la lista desplegable **Lenguaje**, elija el lenguaje de la función.

1. Seleccione **Aceptar**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Establecer un punto de interrupción de función con una dirección de memoria (solo C++ nativo)
 La dirección de un objeto se puede usar para establecer un punto de interrupción en un método llamado por una instancia específica de una clase.  Por ejemplo, dado un objeto con dirección de tipo `my_class`, se puede establecer un punto de interrupción de función en el método `my_method` al que la instancia llama.

1. Establezca un punto de interrupción en algún lugar después de crear una instancia de la instancia de clase.

2. Busque la dirección de la instancia (por ejemplo, `0xcccccccc`).

3. Seleccione **Depurar** > **Nuevo punto de interrupción** > **Punto de interrupción de función** o presione **Alt**+**F9** > **Ctrl**+**B**.

4. Agregue lo siguiente al cuadro **Nombre de la función** y seleccione el lenguaje **C++** .

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Establecer puntos de interrupción de datos (.NET Core 3.0 o posterior)

Los puntos de interrupción de datos interrumpen la ejecución cuando la propiedad de un objeto concreto cambia.

**Para establecer un punto de interrupción de datos**

1. En un proyecto de .NET Core, inicie la depuración y espere hasta que se alcance un punto de interrupción.

2. En las ventanas **Automático**, **Inspección** o **Variables locales**, haga clic con el botón derecho en una propiedad y seleccione **Interrumpir cuando cambia el valor** en el menú contextual.

    ![Punto de interrupción de datos administrado](../debugger/media/managed-data-breakpoint.png "Punto de interrupción de datos administrado")

Los puntos de interrupción de datos en .NET Core no funcionarán con los siguientes elementos:

- Propiedades que no se pueden expandir en las ventanas Variables locales, Automático, Inspección o de información sobre herramientas
- Variables estáticas
- Clases con el atributo DebuggerTypeProxy
- Campos dentro de structs

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Establecer puntos de interrupción de datos (solo C++ nativo)

 Los puntos de interrupción de datos interrumpen la ejecución cuando se produce un cambio en un valor que está almacenado en una ubicación especificada de la memoria. Si el valor se lee pero no cambia, la ejecución no se interrumpe.

**Para establecer un punto de interrupción de datos:**

1. En un proyecto de C++, inicie la depuración y espere hasta que se alcance un punto de interrupción. En el menú **Depurar**, elija **Nuevo punto de interrupción** > **Punto de interrupción de datos**.

    También puede seleccionar **Nuevo** > **Punto de interrupción de datos** en la ventana **Puntos de interrupción** o hacer clic con el botón derecho en un elemento de las ventanas **Automático**, **Inspección** o **Variables locales** y seleccionar **Interrumpir cuando cambia el valor** en el menú contextual.

2. En el cuadro **Dirección**, escriba una dirección de la memoria o una expresión que se evalúe como una dirección de memoria. Por ejemplo, escriba `&avar` para que se produzca una interrupción cuando cambie el contenido de la variable `avar` .

3. En el desplegable **Recuento de bytes** , seleccione el número de bytes que desea que el depurador inspeccione. Por ejemplo, si selecciona **4**, el depurador inspeccionará cuatro bytes a partir de `&avar` e interrumpirá la ejecución si alguno de esos bytes cambia de valor.

Los puntos de interrupción de datos no funcionan en las siguientes condiciones:
- Si un proceso que no se está depurando escribe en la ubicación de la memoria.
- Si la ubicación de la memoria se comparte entre dos o más procesos.
- Si la ubicación de la memoria se actualiza dentro del kernel. Por ejemplo, si se pasa memoria a la función `ReadFile` de Windows de 32 bits, la memoria se actualizará desde el modo kernel, con lo cual el depurador no se detendrá en la actualización.
- Cuando la expresión de inspección sea superior a 4 bytes en un hardware de 32 bits y a 8 bytes en un hardware de 64 bits. Se trata de una limitación de la arquitectura x86.

> [!NOTE]
> - Los puntos de interrupción de datos dependen de direcciones de memoria específicas. La dirección de una variable cambia de una sesión de depuración a la siguiente, por lo que los puntos de interrupción de datos se deshabilitan automáticamente al final de cada sesión de depuración.
>
> - Si se establece un punto de interrupción de datos en una variable local, el punto de interrupción se mantiene habilitado cuando finaliza la función, pero la dirección de memoria ya no es aplicable, por lo que el comportamiento del punto de interrupción es imprevisible. Si se establece un punto de interrupción de datos en una variable local, se recomienda eliminarlo o deshabilitarlo antes de que finalice la función.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Administrar puntos de interrupción en la ventana Puntos de interrupción

 En la ventana **Puntos de interrupción** se pueden ver y administrar todos los puntos de interrupción de la solución. Esta ubicación centralizada es especialmente útil en una solución grande o en escenarios de depuración complejos en los que los puntos de interrupción son críticos.

En la ventana **Puntos de interrupción** se pueden buscar, ordenar, filtrar, habilitar/deshabilitar o eliminar puntos de interrupción. También se pueden establecer condiciones y acciones, o agregar una nueva función o un punto de interrupción de datos.

Para abrir la ventana **Puntos de interrupción**, seleccione **Depurar** > **Ventanas** > **Puntos de interrupción**, o bien presione **Alt**+**F9** o **Ctrl**+**Alt**+**B**.

![Ventana Puntos de interrupción](../debugger/media/breakpointswindow.png "ventana Puntos de interrupción")

Para seleccionar las columnas que se van a mostrar en la ventana **Puntos de interrupción**, seleccione **Mostrar columnas**. Seleccione un encabezado de columna para ordenar la lista de puntos de interrupción por esa columna.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etiquetas de puntos de interrupción
Se pueden usar etiquetas para ordenar y filtrar la lista de puntos de interrupción en la ventana **Puntos de interrupción**.

1. Para agregar una etiqueta a un punto de interrupción, haga clic con el botón derecho en el punto de interrupción en el código fuente o en la ventana **Puntos de interrupción** y, después, seleccione **Editar etiquetas**. Agregue una etiqueta nueva o elija una existente y, después, seleccione **Aceptar**.
2. Para ordenar la lista de puntos de interrupción en la ventana **Puntos de interrupción**, seleccione **Etiquetas**, **Condiciones** u otros encabezados de columna. Para elegir las columnas que se van a mostrar, seleccione **Mostrar columnas** en la barra de herramientas.

### <a name="export-and-import-breakpoints"></a>Exportar e importar puntos de interrupción
 Para guardar o compartir el estado y la ubicación de los puntos de interrupción, puede exportarlos o importarlos.

- Para exportar un solo punto de interrupción a un archivo XML, haga clic con el botón derecho en el punto de interrupción en el código fuente o en la ventana **Puntos de interrupción** y, luego, seleccione **Exportar** o **Exportar seleccionados**. Elija una ubicación de exportación y, después, seleccione **Guardar**. La ubicación predeterminada es la carpeta de la solución.
- Para exportar varios puntos de interrupción, active las casillas situadas junto a los puntos de interrupción en la ventana **Puntos de interrupción** o especifique los criterios de búsqueda que quiera en el campo **Buscar**. Seleccione el icono **Exportar todos los puntos de interrupción que coinciden con el criterio de búsqueda actual** y guarde el archivo.
- Para exportar todos los puntos de interrupción, desactive todas las casillas y deje el campo **Buscar** en blanco. Seleccione el icono **Exportar todos los puntos de interrupción que coinciden con el criterio de búsqueda actual** y guarde el archivo.
- Para importar puntos de interrupción, seleccione el icono **Importar puntos de interrupción de un archivo** en la ventana **Puntos de interrupción**, vaya a la ubicación del archivo XML y seleccione **Abrir**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Establecer puntos de interrupción desde las ventanas del depurador

También se pueden establecer puntos de interrupción en las ventanas del depurador **Pila de llamadas** y **Desensamblado**.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Establecer un punto de interrupción en la ventana Pila de llamadas

 Para interrumpir la ejecución en la instrucción o línea a la que una función de llamada regresa, se puede establecer un punto de interrupción en la ventana **Pila de llamadas**.

**Para establecer un punto de interrupción en la ventana Pila de llamadas:**

1. Para abrir la ventana **Pila de llamadas**, la depuración debe estar en pausa. Seleccione **Depurar** > **Ventanas** > **Pila de llamadas** o presione **Ctrl**+**Alt**+**C**.

2. En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función de llamada y seleccione **Punto de interrupción** > **Insertar punto de interrupción** o presione **F9**.

   Aparecerá un símbolo de punto de interrupción junto al nombre de la llamada de función en el margen izquierdo de la pila de llamadas.

El punto de interrupción de la pila de llamadas aparece en la ventana **Puntos de interrupción** como una dirección, con una ubicación de memoria que se corresponde con la siguiente instrucción ejecutable de la función.

El depurador interrumpe la ejecución en la instrucción.

Para más información sobre la pila de llamadas, vea [Procedimiento para usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

Si quiere realizar un seguimiento visual de los puntos de interrupción durante la ejecución del código, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Establecer un punto de interrupción en la ventana Desensamblado

1. Para abrir la ventana **Desensamblado**, la depuración debe estar en pausa. Seleccione **Depurar** > **Ventanas** > **Desensamblado** o presione **Alt**+**8**.

2. En la ventana **Desensamblado**, haga clic en el margen izquierdo de la instrucción que quiera interrumpir. También puede seleccionarlo y presionar **F9**, o bien hacer clic con el botón derecho y seleccionar **Punto de interrupción** > **Insertar punto de interrupción**.

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Escribir mejor código de C# con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Solución de problemas de puntos de interrupción en el depurador de Visual Studio](../debugger/troubleshooting-breakpoints.md)
