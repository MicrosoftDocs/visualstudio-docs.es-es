---
title: "Utilizar puntos de interrupción en el depurador de Visual Studio | Documentos de Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 95c6f87e120cd8a62aa3959548f968b70c820d39
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Utilizar puntos de interrupción en el depurador de Visual Studio
Los puntos de interrupción detienen la ejecución del depurador para, por ejemplo, ver el estado de las variables de código o examinar la pila de llamadas. Constituyen una de las técnicas de depuración más importantes en los cuadros de herramientas de los desarrolladores.  
  
##  <a name="BKMK_Overview"></a> Establecer un punto de interrupción en código fuente  
 Establecer un punto de interrupción en el código fuente haciendo clic en el margen izquierdo de un archivo de código fuente o coloque el cursor en una línea de código y presione F9. El punto de interrupción aparece como un punto rojo en el margen izquierdo y la línea de código se muestra coloreada:  
  
 ![Establecer un punto de interrupción](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Cuando se ejecuta este código en el depurador, la ejecución se detiene al alcanzar el punto de interrupción y antes de ejecutarse el código de esa línea. La línea de código fuente aparece coloreada de amarillo:  
  
 ![Ejecución de punto de interrupción detenida](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 En este punto, el valor de `testInt` sigue siendo 1.  
  
 Puede consultar el estado actual de la aplicación, incluidos los valores de variable y la pila de llamadas. Para más información sobre la pila de llamadas, vea [How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md).  
  
 Los puntos de interrupción pueden establecerse en cualquier línea de código ejecutable. Por ejemplo, en el código de C# anterior se puede establecer un punto de interrupción en la declaración de variable, en el bucle `for` o en cualquier código incluido dentro del bucle `for` , pero no en las declaraciones de clase o espacio de nombres ni en la signatura del método.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Establecer un punto de interrupción de función  
  Se puede interrumpir la ejecución cuando se llama a una función.
  
1. Abra la **puntos de interrupción** ventana y elija **nuevo > punto de interrupción de función**.

2. Escriba un nombre de función en la **nombre de la función** cuadro. 

   Para reducir el número de la especificación de función:
   
   Utilice el nombre de función completo. 
   Ejemplo: Namespace1.ClassX.MethodA()
   
   Agregue los tipos de parámetro de una función sobrecargada. 
   Ejemplo: MethodA (int, string)
   
   Use la '!' símbolo para especificar el módulo.
   Ejemplo: App1.dll! MethodA
   
   Utilice el operador de contexto en C++ nativo.
   {función, [módulo]} [+&lt;desplazamiento de línea desde el inicio del método&gt;] ejemplo: {MethodA, App1.dll}+2

3. En el **lenguaje** de lista desplegable, elija el idioma específico de la función que desea interrumpir en.
  
##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Establecer otros tipos de puntos de interrupción  
 También se pueden establecer puntos de interrupción en la pila de llamadas, en la ventana Desensamblado y, en código de C++ nativo, en una condición de datos o dirección de memoria.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Establecer un punto de interrupción en la ventana Pila de llamadas  
 Puede interrumpir la ejecución en la instrucción o línea que devuelve una función de llamada para establecer un punto de interrupción en la ventana **Pila de llamadas** . Para más información sobre la pila de llamadas, vea [How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md). El depurador debe estar detenido.  
  
1.  Empiece a depurar la aplicación y espere a que se detenga la ejecución (por ejemplo, en un punto de interrupción). Abra la **pila de llamadas** ventana (**Depurar > Windows > pila de llamadas**, o **CTRL + ALT + C**).  
  
2.  Haga clic en la función que realiza la llamada y, a continuación, seleccione **punto de interrupción > Insertar punto de interrupción**, o simplemente utilizar la tecla de método abreviado **F9**.  
  
3.  En el margen izquierdo de la pila de llamadas, junto al nombre de la llamada de función, aparece un símbolo de punto de interrupción.  
  
 En la ventana **Puntos de interrupción** , el punto de interrupción de la pila de llamadas aparecerá como una dirección con una ubicación de memoria que corresponde a la siguiente instrucción ejecutable de la función. El depurador interrumpe la ejecución en la instrucción.  
  
 Visualmente traza los puntos de interrupción durante la ejecución de código, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Establecer un punto de interrupción en la ventana Desensamblado  
 Para establecer un punto de interrupción en una instrucción de ensamblado, el depurador debe hallarse en modo de interrupción.  
  
1.  Empiece a depurar la aplicación y espere a que se detenga la ejecución (por ejemplo, en un punto de interrupción). Abra la **desensamblado** ventana (**Depurar > Windows > desensamblado**, o **Ctrl + Alt + D**).  
  
2.  Haga clic en el margen izquierdo de la instrucción donde desea establecer un punto de interrupción o coloque el cursor en la instrucción y presione **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Establecer un punto de interrupción de datos (solo C++ nativo)  
 Los puntos de interrupción de datos interrumpen la ejecución cuando se produce un cambio en un valor que está almacenado en una ubicación especificada de la memoria. Si el valor se lee pero no cambia, la ejecución no se interrumpe. Para establecer puntos de interrupción de datos, el depurador debe estar en modo de interrupción.  
  
1.  Empiece a depurar la aplicación y espere hasta que se alcance un punto de interrupción. En el **depurar** menú, elija **nuevo punto de interrupción > punto de interrupción de datos** (o abra el **puntos de interrupción** ventana y elija **nuevo > punto de interrupción de datos**.  
  
2.  En el cuadro **Dirección** , escriba una dirección de la memoria o una expresión que se evalúe como una dirección de memoria. Por ejemplo, escriba `&avar` para que se produzca una interrupción cuando cambie el contenido de la variable `avar` .  
  
3.  En el desplegable **Recuento de bytes** , seleccione el número de bytes que desea que el depurador inspeccione. Por ejemplo, si selecciona **4**, el depurador inspeccionará cuatro bytes a partir de `&avar` e interrumpirá la ejecución si alguno de esos bytes cambia de valor.  
  
 Tenga en cuenta que los puntos de interrupción de datos dependen de la aplicabilidad de direcciones de memoria específicas.  
  
-   Las direcciones de las variables cambian de una sesión de depuración a la siguiente. Por esta razón, los puntos de interrupción de datos se deshabilitan automáticamente a la finalización de cada sesión de depuración.  
  
-   Si se establece un punto de interrupción de datos en una variable local, el punto de interrupción se mantiene habilitado cuando finaliza la función, pero la dirección de memoria ya no es aplicable, por lo que el comportamiento del punto de interrupción es imprevisible. Si se establece un punto de interrupción de datos en una variable local, se recomienda quitarlo o deshabilitarlo antes de que finalice la función.  
  
 Los puntos de interrupción de datos no funcionan en estas condiciones:  
  
-   Si un proceso que no se está depurando escribe en la ubicación de la memoria.  
  
-   Si la ubicación de la memoria se comparte entre dos o más procesos.  
  
-   Si la ubicación de la memoria se actualiza dentro del kernel. Por ejemplo, si se pasa memoria a la función `ReadFile` de Windows de 32 bits, la memoria se actualizará desde el modo kernel y el depurador no interrumpirá su ejecución en la escritura de memoria.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Establecer un punto de interrupción con una dirección de memoria (solo en C++ nativo)  
 También puede usar la dirección de un objeto para establecer un punto de interrupción en un método llamado en una instancia específica de una clase.  Por ejemplo:  
  
 Por ejemplo, dado un objeto de tipo `my_class` con la dirección, puede establecer un punto de interrupción de función en un método denominado `my_method` llamado desde esa instancia.  
  
1.  Establezca un punto de interrupción en algún lugar después de crear una instancia de dicha instancia de clase.  
  
2.  Busque la dirección de la instancia (digamos que es `0xcccccccc`).  
  
3.  Haga clic en **Depurar > nuevo punto de interrupción > punto de interrupción de función** (o **ALT + F9, B**).  
  
4.  Agregue el siguiente texto para el cuadro **Nombre de la función** :  
  
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Administrar puntos de interrupción  
 Puede usar el **puntos de interrupción** ventana (**Depurar > Windows > puntos de interrupción**, o **CTRL + ALT + B**) para ver todos los puntos de interrupción ha establecido en la solución:  
  
 ![Ventana puntos de interrupción](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 La ventana **Puntos de interrupción** proporciona una ubicación central desde la que administrar todos los puntos de interrupción, algo especialmente útil cuando se tiene una solución grande o un escenario de depuración complejo en el que los puntos de interrupción son muy importantes. Si es necesario guardar o compartir el estado y la ubicación de un conjunto de puntos de interrupción, estos puntos de interrupción solo se pueden exportar e importar desde la ventana **Puntos de interrupción** .  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Puntos de interrupción avanzados  
  
## <a name="breakpoint-conditions"></a>Condiciones de punto de interrupción  
 La definición de condiciones le permite controlar cuándo y dónde se ejecuta un punto de interrupción.  
  
1.  Haga clic con el botón derecho en el punto de interrupción o mantenga el puntero y elija el icono de configuración.  
  
2.  En el menú contextual, seleccione **Condiciones**. Se abrirá la ventana **Configuración del punto de interrupción** :  
  
 ![Configuración de punto de interrupción](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
 Al activar la casilla **Condiciones** , la ventana se expande para mostrar los diferentes tipos de condiciones.  
  
 **Expresión condicional:** si se selecciona “Expresión condicional”, se pueden elegir dos condiciones, **Es true** y **Cuando cambie**. Elija **Es true** si desea interrumpir cuando la expresión se cumple o elija **Cuando cambie** si desea interrumpir cuando el valor de la expresión cambie.  
  
 En el siguiente ejemplo, el punto de interrupción se alcanza únicamente cuando el valor de `testInt` es **4**:  
  
 ![Condición de punto de interrupción es verdadera](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
 En el siguiente ejemplo, el punto de interrupción se alcanza únicamente cuando el valor de `testInt` cambia:  
  
 ![Punto de interrupción cuando cambie](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
 El comportamiento del campo “Cuando cambie” es diferente según el lenguaje de programación. Si elige **Cuando cambie** para el código nativo, el depurador no considerará la primera evaluación de la condición como cambio, por lo que no se visitará el punto de interrupción en la primera evaluación. Si elige **cuando cambia** para código administrado, el punto de interrupción en la primera evaluación después de **cuando cambia** está seleccionada.  
  
 Si se establece una condición de punto de interrupción con una sintaxis no válida, aparecerá un mensaje de advertencia. Si se especifica una condición de punto de interrupción con una sintaxis válida pero una semántica no válida, aparecerá un mensaje de advertencia la primera vez que se visite el punto de interrupción. En ambos casos, el depurador interrumpirá la ejecución cuando se visite el punto de interrupción no válido. El punto de interrupción se omitirá únicamente si la condición es válida y se evalúa como `false`.  
  
 La condición puede ser cualquier expresión válida que reconozca el depurador. Para más información sobre las expresiones válidas, vea [Expressions in the Debugger](../debugger/expressions-in-the-debugger.md).  

> [!NOTE]
> Puede usar **CTRL+ENTRAR** para cerrar el **configuración de punto de interrupción** ventana.
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Usar identificadores de objeto en las condiciones de punto de interrupción (C# y F #)  
 Hay veces en las quiere observar el comportamiento de un objeto específico; por ejemplo, podría querer averiguar por qué se insertó un objeto más de una vez en una colección. En C# y F#, puede crear identificadores de objeto para instancias específicas de [tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types) y usarlos en condiciones de punto de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.  Para crear un identificador de objeto, haga lo siguiente:  
  
1.  Establezca un punto de interrupción en el código después de que se haya creado el objeto.  
  
2.  Inicie la depuración y cuando se detenga la ejecución en el punto de interrupción, busque el punto de interrupción en la ventana **Locales** , haga clic con el botón derecho en él y seleccione **Crear el identificador del objeto**.  
  
     Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Este es el identificador del objeto.  
  
3.  Agregue un nuevo punto de interrupción condicional en el punto que quiere investigar (por ejemplo, cuando se agregue el objeto a la colección).  
  
4.  Use el identificador de objeto en el campo de expresión condicional. Por ejemplo, si hay una variable `item` que hace referencia al objeto que se agregará a la colección, tendría que poner **item == $n**, donde **n** es el número de id. de objeto.  
  
     La ejecución se interrumpirá en el punto cuando ese objeto se agregue a la colección.  
  
 Si más adelante quiere eliminar el identificador de objeto, haga clic con el botón derecho en la variable en la ventana **Locales** y seleccione **Eliminar el identificador del objeto**.  
  
 Tenga en cuenta que los identificadores de objeto crean referencias débiles y no impiden que el objeto se recopile como elemento no usado. Los identificadores de objeto solo son válidos para la sesión de depuración actual.  
  
## <a name="hit-count"></a>Número de llamadas  
 Si sospecha que un bucle del código inicia un comportamiento erróneo después de cierto número de iteraciones, puede establecer un punto de interrupción para detener la ejecución tras un determinado número de visitas a la línea de código, en lugar de verse obligado a presionar repetidamente asociado **F5**  para alcanzar el nivel de iteración.  
  
 En la ventana **Configuración del punto de interrupción** , establezca la condición en **Número de llamadas**. A continuación, puede especificar el número de iteraciones. En el siguiente ejemplo, el punto de interrupción se alcanza únicamente cada dos iteraciones:  
  
 ![Número de llamadas de punto de interrupción](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtro  
 Puede restringir un punto de interrupción para que se active solo en los dispositivos especificados, o bien en los procesos y subprocesos especificados.  
  
 En la ventana **Configuración del punto de interrupción**, establezca la condición en **Filtro**. Escriba una o varias de las siguientes expresiones.  
  
-   MachineName = "name"  
  
-   ProcessId = value  
  
-   ProcessName = "name"  
  
-   ThreadId = value  
  
-   ThreadName = "name"  
  
 Incluya los valores de cadena entre comillas dobles. Puede combinar las cláusulas con `&` (AND), `||` (OR), `!` (NOT) y paréntesis.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Acciones de punto de interrupción y puntos de seguimiento  
 Un punto de seguimiento es un punto de interrupción que imprime un mensaje en la ventana de salida. Un punto de seguimiento puede actuar como una instrucción de seguimiento temporal en el lenguaje de programación.  
  
 En la ventana **Configuración del punto de interrupción** , active la casilla **Acciones** . En el grupo **Acción** , elija **Registrar un mensaje en la ventana de salida** . Puede imprimir una cadena genérica, como **Esto es una prueba**. Para incluir el valor de una variable o expresión, enciérrela entre llaves.  También puede utilizar especificadores de formato ([C#](../debugger/format-specifiers-in-csharp.md) y [C++](../debugger/format-specifiers-in-cpp.md)) para los valores incluidos en un punto de seguimiento.
  
 Para interrumpir la ejecución cuando se alcanza el punto de seguimiento, desactive la casilla **Continuar la ejecución** . Si se activa **Continuar la ejecución** , la ejecución no se detiene. En ambos casos, se imprime el mensaje.  
  
 Puede usar las siguientes palabras clave especiales en el **Mensaje**.  
  
|||  
|-|-|  
|**$ADDRESS**|Instrucción actual|  
|**$CALLER**|Nombre de la función de llamada|  
|**$CALLSTACK**|Pila de llamadas|  
|**$FUNCTION**|Nombre de la función actual|  
|**$PID**|Identificador de proceso|  
|**$PNAME**|Nombre del proceso|  
|**$TID**|Identificador del subproceso|  
|**$TNAME**|Nombre del subproceso|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etiquetas de puntos de interrupción  
 Las etiquetas de punto de interrupción solo se utilizan en la ventana **Puntos de interrupción** para ordenar y filtrar la lista de puntos de interrupción. Para agregar una etiqueta a un punto de interrupción, elija la fila del punto de interrupción y elija **Etiqueta** en el menú contextual.  
  
## <a name="export-and-import-breakpoints"></a>Exportar e importar puntos de interrupción  
 Los puntos de interrupción se pueden exportar a un archivo XML; para ello, haga clic con el botón derecho en el punto de interrupción y seleccione **Exportar**. El archivo se guarda de forma predeterminada en el directorio de la solución. Para importar puntos de interrupción, abra la ventana **Puntos de interrupción** (**CTRL+ALT+B**) y, en la barra de herramientas, haga clic en la flecha que apunta a la derecha (la información sobre herramientas es **Importar puntos de interrupción de un archivo**).  
  
## <a name="see-also"></a>Vea también  
[Solucionar problemas de puntos de interrupción en el depurador de Visual Studio](../debugger/troubleshooting-breakpoints.md)  
[Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)
