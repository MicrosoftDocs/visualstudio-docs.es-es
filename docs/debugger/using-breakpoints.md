---
title: Usar puntos de interrupción en el depurador | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
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
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187322"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usar puntos de interrupción en el depurador de Visual Studio

Los puntos de interrupción son una de las técnicas de depuración más importantes del cuadro de herramientas del desarrollador. Establezca puntos de interrupción donde desee pausar la ejecución del depurador. Por ejemplo, puede que desee ver el estado de las variables de código o examinar la pila de llamadas en un punto de interrupción determinado.  Si está intentando resolver una advertencia o un problema mientras usa puntos de interrupción, vea [solucionar problemas de puntos de interrupción en el depurador de Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Si conoce la tarea o el problema que está intentando resolver, pero necesita saber qué tipo de punto de interrupción usar, vea [Buscar la tarea de depuración](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="BKMK_Overview"></a>Establecer puntos de interrupción en el código fuente

Los puntos de interrupción pueden establecerse en cualquier línea de código ejecutable. Por ejemplo, en el código C# siguiente, puede establecer un punto de interrupción en la declaración de la variable, en el`for`bucle o en cualquier código dentro del bucle de`for`. No se puede establecer un punto de interrupción en las declaraciones de clase o espacio de nombres o en la firma del método.

Para establecer un punto de interrupción en el código fuente, haga clic en el margen izquierdo situado junto a una línea de código. También puede seleccionar la línea y presionar **F9**, seleccionar **depurar** > **alternar punto de interrupción**o hacer clic con el botón derecho y seleccionar **punto de interrupción** > **Insertar punto de interrupción**. El punto de interrupción aparece como un punto rojo en el margen izquierdo.

Para la mayoría de C#los lenguajes, incluidos los puntos de interrupción y las líneas de ejecución actuales se resaltan automáticamente. En C++ el código, puede activar el resaltado de puntos de interrupción y las líneas actuales seleccionando **herramientas** (o **depurar**) > **Opciones** > **depuración** >  **resaltar la línea de código fuente para los puntos de interrupción y actuales Statement (C++ solo)** .

![Establecer un punto de interrupción](../debugger/media/basicbreakpoint.png "Punto de interrupción básico")

Al depurar, la ejecución se detiene en el punto de interrupción antes de que se ejecute el código de esa línea. El símbolo de punto de interrupción muestra una flecha amarilla.

En el punto de interrupción en el ejemplo siguiente, el valor de `testInt` sigue siendo 1. Por lo tanto, el valor no ha cambiado desde que la variable se inicializó (se estableció en un valor de 1) porque la instrucción en amarillo todavía no se ha ejecutado.

![Ejecución de punto de interrupción detenida](../debugger/media/breakpointexecution.png "Ejecución de puntos de interrupción")

Cuando el depurador se detiene en el punto de interrupción, puede examinar el estado actual de la aplicación, incluidos [los valores](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) de las variables y la [pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

Estas son algunas instrucciones generales para trabajar con puntos de interrupción.

- El punto de interrupción es un comando de alternancia. Puede hacer clic en él, presionar **F9**o usar **depurar** > **alternar punto de interrupción** para eliminarlo o volver a insertarlo.

- Para deshabilitar un punto de interrupción sin eliminarlo, desplace el puntero sobre él o haga clic con el botón derecho en él y seleccione **deshabilitar punto de interrupción**. Los puntos de interrupción deshabilitados aparecen como puntos vacíos en el margen izquierdo o en la ventana **puntos de interrupción** . Para volver a habilitar un punto de interrupción, mantenga el mouse sobre él o haga clic con el botón derecho en él y seleccione **Habilitar punto de interrupción**.

- Establezca condiciones y acciones, agregue y edite etiquetas o exporte un punto de interrupción haciendo clic con el botón derecho en él y seleccionando el comando adecuado, o manteniendo el mouse sobre él y seleccionando el icono de **configuración** .

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Acciones de punto de interrupción y puntos de seguimiento

Un *punto de seguimiento* es un punto de interrupción que imprime un mensaje en la ventana **Salida**. Un punto de seguimiento puede actuar como una instrucción de seguimiento temporal en el lenguaje de programación y no pausa la ejecución del código. Para crear un punto de seguimiento, establezca una acción especial en la ventana **configuración del punto de interrupción** . Para obtener instrucciones detalladas, vea [usar puntos de seguimiento en el depurador de Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Condiciones de punto de interrupción

La definición de condiciones le permite controlar cuándo y dónde se ejecuta un punto de interrupción. La condición puede ser cualquier expresión válida que reconozca el depurador. Para más información sobre las expresiones válidas, vea [Expresiones en el depurador de Visual Studio](../debugger/expressions-in-the-debugger.md).

**Para establecer una condición de punto de interrupción:**

1. Haga clic con el botón secundario en el símbolo del punto de interrupción y seleccione **condiciones**. O mantenga el puntero sobre el símbolo de punto de interrupción, seleccione el icono de **configuración** y, a continuación, seleccione **condiciones** en la ventana **configuración del punto de interrupción** .

   También puede establecer condiciones en la ventana **puntos de interrupción** haciendo clic con el botón secundario en un punto de interrupción y seleccionando **configuración**y, después, seleccionando **condiciones**.

   ![Configuración del punto de interrupción](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. En el menú desplegable, seleccione **expresión condicional**, **número de llamadas**o **filtro**y establezca el valor en consecuencia.

3. Seleccione **cerrar** o presione **Ctrl**+**entrar** para cerrar la ventana de **configuración del punto de interrupción** . O bien, en la ventana **puntos de interrupción** , seleccione **Aceptar** para cerrar el cuadro de diálogo.

Los puntos de interrupción con condiciones establecidas aparecen con un símbolo **+** en las ventanas código fuente y **puntos de interrupción** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Crear una expresión condicional

Al seleccionar **expresión condicional**, puede elegir entre dos condiciones: **es true** o cuando se **cambia**. Elija **es true** para interrumpir cuando se cumple la expresión o **cuando cambia** para interrumpir cuando el valor de la expresión ha cambiado.

En el ejemplo siguiente, solo se alcanza el punto de interrupción cuando el valor de `testInt` es **4**:

![La condición del punto de interrupción es true](../debugger/media/breakpointconditionistrue.png "El punto de interrupción es true")

En el ejemplo siguiente, solo se alcanza el punto de interrupción cuando el valor de `testInt` cambia:

![Punto de interrupción cuando se cambia](../debugger/media/breakpointwhenchanged.png "Punto de interrupción cuando se cambia")

Si se establece una condición de punto de interrupción con una sintaxis no válida, aparecerá un mensaje de advertencia. Si se especifica una condición de punto de interrupción con una sintaxis válida pero una semántica no válida, aparecerá un mensaje de advertencia la primera vez que se visite el punto de interrupción. En cualquier caso, el depurador se interrumpe cuando llega al punto de interrupción no válido. El punto de interrupción se omitirá únicamente si la condición es válida y se evalúa como `false`.

>[!NOTE]
>El comportamiento del campo **Cuando cambie** es diferente según el lenguaje de programación.
>- En el caso de código nativo, el depurador no considera la primera evaluación de la condición como un cambio, por lo que no alcanza el punto de interrupción en la primera evaluación.
>- En el caso de código administrado, el depurador alcanza el punto de interrupción en la primera evaluación después de seleccionar **cuando se cambia** .

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Usar identificadores de objeto en expresionesC# condicionales (solo y F# )

 Hay ocasiones en las que desea observar el comportamiento de un objeto concreto. Por ejemplo, podría querer averiguar por qué se insertó un objeto en una colección más de una vez. En C# y F#, puede crear identificadores de objeto para instancias específicas de [tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types) y usarlos en condiciones de punto de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.

**Para crear un identificador de objeto:**

1. Establezca un punto de interrupción en el código una vez que se haya creado el objeto.

2. Inicie la depuración y, cuando la ejecución se pausa en el punto de interrupción, seleccione **Depurar** > **Windows** > **variables locales** o **Alt**+**4** para abrir la ventana **variables locales** .

   Busque la instancia de objeto específica en la ventana **variables locales** , haga clic con el botón derecho en ella y seleccione **Crear identificador de objeto**.

   Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Este es el identificador del objeto.

3. Agregue un nuevo punto de interrupción en el punto que desea investigar; por ejemplo, cuando el objeto se va a agregar a la colección. Haga clic con el botón derecho en el punto de interrupción y seleccione **Condiciones**.

4. Use el identificador de objeto en el campo **Expresión condicional**. Por ejemplo, si la variable `item` es el objeto que se va a agregar a la colección, seleccione **es true** y escriba **Item = = $\<n >** , donde \<n > es el número de ID. del objeto.

   La ejecución se interrumpirá en el punto cuando ese objeto se agregue a la colección.

   Para eliminar el identificador de objeto, haga clic con el botón derecho en la variable en la ventana **variables locales** y seleccione **eliminar ID**. de objeto.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles y no impiden que el objeto se recopile en la recolección de elementos no utilizados. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

### <a name="set-a-hit-count-condition"></a>Establecer una condición de número de llamadas

Si sospecha que un bucle del código inicia un comportamiento erróneo después de cierto número de iteraciones, puede establecer un punto de interrupción para detener la ejecución después de ese número de visitas, en lugar de tener que presionar repetidamente **F5** para llegar a esa iteración.

En **condiciones** en la ventana **configuración del punto de interrupción** , seleccione número de **llamadas**y, a continuación, especifique el número de iteraciones. En el siguiente ejemplo, el punto de interrupción se establece para que se presione en cada iteración:

![Número de llamadas de punto de interrupción](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Establecer una condición de filtro

Puede restringir un punto de interrupción para que se active solo en los dispositivos especificados, o bien en los procesos y subprocesos especificados.

En **condiciones** en la ventana **configuración del punto de interrupción** , seleccione **filtrar**y, a continuación, escriba una o varias de las siguientes expresiones:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Incluya los valores de cadena entre comillas dobles. Puede combinar las cláusulas con `&` (AND), `||` (OR), `!` (NOT) y paréntesis.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Establecer puntos de interrupción de función

Puede interrumpir la ejecución cuando se llama a una función. Esto resulta útil, por ejemplo, cuando se conoce el nombre de la función, pero no su ubicación. También resulta útil si tiene funciones con el mismo nombre y desea interrumpirlas todas (por ejemplo, funciones sobrecargadas o funciones en proyectos diferentes).

**Para establecer un punto de interrupción de función:**

1. Seleccione **Depurar** > **nuevo punto** de interrupción > **función punto de interrupción**o presione **Alt**+**F9** > **Ctrl**+**B**.

   También puede seleccionar **nuevo** > **punto de interrupción de función** en la ventana puntos de **interrupción** .

1. En el cuadro de diálogo **nueva función punto de interrupción** , escriba el nombre de la función en el cuadro **nombre de función** .

   Para restringir la especificación de la función:

   - Use el nombre completo de la función.

     Ejemplo:  `Namespace1.ClassX.MethodA()`

   - Agregue los tipos de parámetro de una función sobrecargada.

     Ejemplo:  `MethodA(int, string)`

   - Use el símbolo '! ' para especificar el módulo.

     Ejemplo: `App1.dll!MethodA`

   - Usar el operador de contexto en C++nativo.

     `{function, , [module]} [+<line offset from start of method>]`

     Ejemplo: `{MethodA, , App1.dll}+2`

1. En la lista desplegable **idioma** , elija el idioma de la función.

1. Seleccione **Aceptar**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Establecer un punto de interrupción de función mediante una dirección C++ de memoria (solo nativo)
 Puede utilizar la dirección de un objeto para establecer un punto de interrupción de función en un método llamado por una instancia específica de una clase.  Por ejemplo, dado un objeto direccionable de tipo `my_class`, puede establecer un punto de interrupción de función en el método `my_method` al que llama la instancia.

1. Establezca un punto de interrupción en algún lugar después de crear una instancia de la instancia de la clase.

2. Busque la dirección de la instancia (por ejemplo, `0xcccccccc`).

3. Seleccione **Depurar** > **nuevo punto** de interrupción > **función punto de interrupción**o presione **Alt**+**F9** > **Ctrl**+**B**.

4. Agregue lo siguiente al cuadro **nombre de función** y seleccione **C++** idioma.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Establecer puntos de interrupción de datos (.NET Core 3,0 o posterior)

Los puntos de interrupción de datos interrumpen la ejecución cuando cambia la propiedad de un objeto concreto.

**Para establecer un punto de interrupción de datos**

1. En un proyecto de .NET Core, inicie la depuración y espere hasta que se alcance un punto de interrupción.

2. En la ventana **automático**, **inspección**o **variables locales** , haga clic con el botón secundario en una propiedad y seleccione **interrumpir cuando el valor cambie** en el menú contextual.

    ![Punto de interrupción de datos administrados](../debugger/media/managed-data-breakpoint.png "Punto de interrupción de datos administrados")

Los puntos de interrupción de datos en .NET Core no funcionarán para:

- Propiedades que no se pueden expandir en la información sobre herramientas, variables locales, automático o ventana Inspección
- Variables estáticas
- Clases con el atributo DebuggerTypeProxy
- Campos dentro de Structs

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Establecer puntos de interrupción de datos C++ (solo nativo)

 Los puntos de interrupción de datos interrumpen la ejecución cuando cambia un valor almacenado en una dirección de memoria especificada. Si el valor se lee pero no cambia, la ejecución no se interrumpe.

**Para establecer un punto de interrupción de datos:**

1. En un C++ proyecto, inicie la depuración y espere hasta que se alcance un punto de interrupción. En el menú **depurar** , elija **nuevo punto** de interrupción > **punto de interrupción de datos**

    También puede seleccionar **nuevo** > **punto de interrupción de datos** en la ventana puntos de **interrupción** o hacer clic con el botón secundario en un elemento de la ventana **automático**, **inspección**o **variables locales** y seleccionar **interrumpir cuando el valor cambie** en el menú contextual.

2. En el cuadro **Dirección**, escriba una dirección de la memoria o una expresión que se evalúe como una dirección de memoria. Por ejemplo, escriba `&avar` para que se produzca una interrupción cuando cambie el contenido de la variable `avar` .

3. En el desplegable **Recuento de bytes** , seleccione el número de bytes que desea que el depurador inspeccione. Por ejemplo, si selecciona **4**, el depurador inspeccionará cuatro bytes a partir de `&avar` e interrumpirá la ejecución si alguno de esos bytes cambia de valor.

Los puntos de interrupción de datos no funcionan en las siguientes condiciones:
- Si un proceso que no se está depurando escribe en la ubicación de la memoria.
- Si la ubicación de la memoria se comparte entre dos o más procesos.
- Si la ubicación de la memoria se actualiza dentro del kernel. Por ejemplo, si se pasa memoria a la función `ReadFile` de Windows de 32 bits, la memoria se actualizará desde el modo kernel, por lo que el depurador no se interrumpirá en la actualización.
- Donde la expresión de inspección es superior a 4 bytes en el hardware de 32 bits y 8 bytes en el hardware de 64 bits. Se trata de una limitación de la arquitectura x86.

> [!NOTE]
> - Los puntos de interrupción de datos dependen de direcciones de memoria específicas. La dirección de una variable cambia de una sesión de depuración a la siguiente, por lo que los puntos de interrupción de datos se deshabilitan automáticamente al final de cada sesión de depuración.
>
> - Si se establece un punto de interrupción de datos en una variable local, el punto de interrupción se mantiene habilitado cuando finaliza la función, pero la dirección de memoria ya no es aplicable, por lo que el comportamiento del punto de interrupción es imprevisible. Si establece un punto de interrupción de datos en una variable local, debe eliminar o deshabilitar el punto de interrupción antes de que finalice la función.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Administrar puntos de interrupción en la ventana Puntos de interrupción

 Puede usar la ventana **puntos de interrupción** para ver y administrar todos los puntos de interrupción de la solución. Esta ubicación centralizada es especialmente útil en una solución grande o en escenarios de depuración complejos en los que los puntos de interrupción son críticos.

En la ventana **puntos de interrupción** , puede buscar, ordenar, filtrar, habilitar/deshabilitar o eliminar puntos de interrupción. También puede establecer condiciones y acciones, o agregar una nueva función o un punto de interrupción de datos.

Para abrir la ventana **puntos de interrupción** , seleccione **depurar** > puntos de **interrupción**de **Windows** > o presione **Alt**+**F9** o **Ctrl**+**Alt**+**B**.

![Ventana puntos de interrupción](../debugger/media/breakpointswindow.png "ventana Puntos de interrupción")

Para seleccionar las columnas que se van a mostrar en la ventana **puntos de interrupción** , seleccione **Mostrar columnas**. Seleccione un encabezado de columna para ordenar la lista de puntos de interrupción por esa columna.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etiquetas de puntos de interrupción
Puede usar etiquetas para ordenar y filtrar la lista de puntos de interrupción en la ventana **puntos de interrupción** .

1. Para agregar una etiqueta a un punto de interrupción, haga clic con el botón secundario en el punto de interrupción en el código fuente o en la ventana **puntos de interrupción** y, a continuación, seleccione **editar etiquetas**. Agregue una nueva etiqueta o elija una existente y, a continuación, seleccione **Aceptar**.
2. Ordene la lista de puntos de interrupción en la ventana **puntos de interrupción** seleccionando las **etiquetas**, **condiciones**u otros encabezados de columna. Puede seleccionar las columnas que se van a mostrar seleccionando **Mostrar columnas** en la barra de herramientas.

### <a name="export-and-import-breakpoints"></a>Exportar e importar puntos de interrupción
 Para guardar o compartir el estado y la ubicación de los puntos de interrupción, puede exportarlos o importarlos.

- Para exportar un solo punto de interrupción a un archivo XML, haga clic con el botón secundario en el punto de interrupción en la ventana código fuente o **puntos de interrupción** y seleccione **exportar** o **exportar seleccionados**. Seleccione una ubicación de exportación y, a continuación, seleccione **Guardar**. La ubicación predeterminada es la carpeta de la solución.
- Para exportar varios puntos de interrupción, en la ventana **puntos de interrupción** , active las casillas situadas junto a los puntos de interrupción o escriba los criterios de búsqueda en el campo de **búsqueda** . Seleccione el icono **exportar todos los puntos de interrupción que coinciden con el criterio de búsqueda actual** y guarde el archivo.
- Para exportar todos los puntos de interrupción, anule la selección de todos los cuadros y deje el campo de **búsqueda** en blanco. Seleccione el icono **exportar todos los puntos de interrupción que coinciden con el criterio de búsqueda actual** y guarde el archivo.
- Para importar puntos de interrupción, en la ventana **puntos de interrupción** , seleccione el icono **importar puntos de interrupción de un archivo** , vaya a la ubicación del archivo XML y seleccione **abrir**.

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Establecer puntos de interrupción desde ventanas del depurador

También puede establecer puntos de interrupción desde las ventanas **pila de llamadas** y depurador de **desensamblador** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Establecer un punto de interrupción en la ventana pila de llamadas

 Para interrumpir en la instrucción o línea a la que se devuelve una función de llamada, puede establecer un punto de interrupción en la ventana **pila de llamadas** .

**Para establecer un punto de interrupción en la ventana pila de llamadas:**

1. Para abrir la ventana **pila de llamadas** , debe estar en pausa durante la depuración. Seleccione **Depurar** > **pila de llamadas**de **Windows** > o presione **Ctrl**+**Alt**+**C**.

2. En la **ventana pila de llamadas** , haga clic con el botón secundario en la función de llamada y seleccione punto de **interrupción** > **Insertar punto de interrupción**o presione **F9**.

   Aparece un símbolo de punto de interrupción junto al nombre de la llamada de función en el margen izquierdo de la pila de llamadas.

El punto de interrupción de la pila de llamadas aparece en la ventana **puntos de interrupción** como una dirección, con una ubicación de memoria que corresponde a la siguiente instrucción ejecutable de la función.

El depurador se interrumpe en la instrucción.

Para obtener más información sobre la pila de llamadas, vea [Ver la pila de llamadas y usar la ventana Pila de llamadas en el depurador](../debugger/how-to-use-the-call-stack-window.md).

Para realizar un seguimiento visual de los puntos de interrupción durante la ejecución del código, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Establecer un punto de interrupción en la ventana Desensamblado

1. Para abrir la ventana **Desensamblado** , debe estar en pausa durante la depuración. Seleccione **Depurar** > **Windows** > **Desensamblado**o presione **Alt**+**8**.

2. En la ventana **Desensamblado** , haga clic en el margen izquierdo de la instrucción en la que desea interrumpir. También puede seleccionarlo y presionar **F9**, o bien hacer clic con el botón derecho y seleccionar un **punto de interrupción** > **Insertar punto de interrupción**.

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Escriba mejor C# código mediante Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Solucionar problemas de puntos de interrupción en el depurador de Visual Studio](../debugger/troubleshooting-breakpoints.md)
