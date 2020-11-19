---
title: Registro de información con puntos de seguimiento | Microsoft Docs
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 33b471122318038ab66bc4f73e437209c6da2ffe
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2020
ms.locfileid: "89561343"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Registro de información en la ventana de salida mediante puntos de seguimiento en Visual Studio

Los puntos de seguimiento permiten registrar información en la ventana de salida en condiciones configurables sin necesidad de modificar ni detener el código. Esta característica es compatible tanto con los lenguajes administrados (C#, Visual Basic, F#) como con el código nativo, así como lenguajes como JavaScript y Python.

## <a name="let39s-take-an-example"></a>Veamos un ejemplo

El programa de ejemplo siguiente es un bucle `for` sencillo con una variable de contador que se incrementa en uno cada vez que el bucle ejecuta otra iteración.

![Ejemplo de contador](../debugger/media/counterexample.png "Ejemplo de contador")

## <a name="set-tracepoints-in-source-code"></a>Establecimiento de puntos de seguimiento en el código fuente

Para establecer puntos de seguimiento, especifique una cadena de salida en la casilla **Acciones** de la ventana **Configuración del punto de interrupción**.

1. Para inicializar un punto de seguimiento, primero haga clic en el medianil que se encuentra a la izquierda del número de línea donde quiere establecer el punto de seguimiento.

   ![Inicialización del punto de interrupción](../debugger/media/breakpointinitialization.png "Inicialización del punto de interrupción")

2. Mantenga el mouse sobre el círculo rojo y haga clic en el icono de engranaje.
3. Se abrirá la ventana **Configuración del punto de interrupción**.

   ![Ventana Punto de interrupción](../debugger/media/breakpointwindow.png "Ventana Punto de interrupción")

4. Active la casilla **Acciones**.

   ![Casilla Acciones activada](../debugger/media/checkedactionsbox.png "Casilla Acciones activada")

   Observe que el círculo rojo cambia a un diamante que indica que pasó de un punto de interrupción a un punto de seguimiento.

5. Escriba el mensaje que quiere registrar en el cuadro de texto **Mostrar un mensaje en la ventana de salida** (para detalles, consulte las secciones que aparecen más adelante en este artículo).

   El punto de seguimiento ya se estableció. Presione el botón &quot;Cerrar&quot; si solo quiere registrar información en la ventana de salida.

6. Si quiere agregar condiciones que determinen si se muestra el mensaje, active la casilla **Condiciones**.

   ![Casilla Condiciones activada](../debugger/media/checkedconditionsbox.png "Casilla Condiciones activada")

   Tiene tres opciones para las condiciones: **Expresión condicional**, **Filtro** y **Número de llamadas**.

## <a name="actions-menu"></a>Menú Acciones

Este menú le permite registrar un mensaje en la ventana de salida. Escriba las cadenas que quiere mostrar en el cuadro de mensaje (no se necesitan comillas). Si quiere mostrar los valores de las variables, asegúrese de encerrar la variable entre llaves.

Por ejemplo, si quiere mostrar el valor de la variable `counter` en la consola de salida, escriba {counter} en el cuadro de texto del mensaje.

![Mensaje de salida Counter](../debugger/media/counteroutputmessage.png "Mensaje de salida Counter")

Si hace clic en **Cerrar** y luego depura el programa (**F5**), verá la salida siguiente en la ventana de salida.

![Mensaje de acciones en la ventana de salida](../debugger/media/actionsmessageinoutputwindow.png "Mensaje de acciones en la ventana de salida")

También puede usar palabras clave especiales para mostrar información más específica. Escriba la palabra clave tal como se mostró anteriormente (use un carácter "$" antes de cada palabra clave, que debe estar escrita completamente en mayúsculas).

| Palabra clave | Qué se muestra |
| --- | --- |
| $ADDRESS | Instrucción actual |
| $CALLER | Nombre de la función de llamada |
| $CALLSTACK | Pila de llamadas |
| $FUNCTION | Nombre de la función actual |
| $PID | Identificador del proceso |
| $PNAME | Nombre del proceso |
| $TID | Id. de subproceso |
| $TNAME   | Nombre del subproceso |
| $TICK | Contador de réplica (de GetTickCount de Windows) |

## <a name="conditions-menu"></a>Menú de condiciones

Las condiciones permiten filtrar los mensajes de salida, por lo que solo se muestran en determinados escenarios. Hay tres tipos principales de condiciones disponibles.

### <a name="conditional-expression"></a>Expresión condicional
En el caso de una expresión condicional, se muestra un mensaje de salida solo cuando se cumplen ciertas condiciones.

Para las expresiones condicionales, puede establecer el punto de seguimiento para que se genere un mensaje cuando una condición determinada sea verdadera o cuando se haya modificado. Por ejemplo, si solo quiere mostrar el valor del contador durante las iteraciones pares del bucle `for`, puede seleccionar la opción **Is true** y escribir `i%2 == 0` en el cuadro de texto del mensaje.

![Expresión condicional Is True](../debugger/media/conditionalexpressionistrue.png "Expresión condicional Is True")

Si quiere imprimir el valor del contador cuando la interación del bucle `for` cambia, seleccione la opción **When changed** y escriba `i` en el cuadro de texto del mensaje.

![Expresión condicional When Changed](../debugger/media/conditionalexpressionwhenchanged.png "Expresión condicional When Changed")

El comportamiento de la opción **When changed** es distinto según el lenguaje de programación.

- El depurador no considerará la primera evaluación de la condición como cambio, por lo que no se llega al punto de seguimiento en la primera evaluación.
- En el código administrado, el depurador visita el punto de seguimiento en la primera evaluación después de que se selecciona **When changed**.

Para una visión más completa de las expresiones válidas que se pueden usar al establecer las condiciones, consulte [Expresiones en el depurador](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Número de llamadas
Una condición de número de llamadas permite enviar la salida solo después de que la línea de código donde se establece el punto de seguimiento se haya ejecutado un número especificado de veces.

En el caso del número de llamadas, puede elegir que se genere un mensaje cuando la línea de código donde se establece el punto de seguimiento se haya ejecutado un número de veces que sea igual o mayor que el valor del número de llamadas especificado o que sea un múltiplo de este valor. Elija la opción que mejor se adapte a sus necesidades y escriba un valor entero en el campo (por ejemplo, 5) que represente la iteración de interés.

![Expresión condicional Número de llamadas](../debugger/media/conditionalexpressionhitcount.png "Expresión condicional Número de llamadas")

### <a name="filter"></a>Filtro
En el caso de una condición de filtro, especifique para qué dispositivos, procesos o subprocesos se muestra la salida.

![Expresión condicional Filtro](../debugger/media/conditionalexpressionfilter.png "Expresión condicional Filtro")

Lista de las expresiones de filtro:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Escriba las cadenas (como los nombres) entre comillas dobles. Los valores se pueden escribir sin comillas. Puede combinar las cláusulas con `&` (`AND`), `||` (`OR`), `!` (`NOT`) y paréntesis.

## <a name="considerations"></a>Consideraciones

Aunque los puntos de seguimiento están diseñados para que la experiencia de depuración sea más limpia y más fluida, hay algunas consideraciones que debe tener en cuenta cuando se trata de usarlos.

A veces, cuando inspecciona alguna propiedad o atributo de un objeto, es posible que su valor cambie. Si el valor cambia durante la inspección, no es un error causado por la característica de punto de seguimiento misma. Sin embargo, el uso de puntos de seguimiento para inspeccionar objetos no impide estas modificaciones accidentales.

La manera en que las expresiones se evalúan en el cuadro de mensaje **Acción** puede ser distinto del lenguaje que usa actualmente para desarrollo. Para generar una cadena, por ejemplo, no necesita encapsular un mensaje entre comillas incluso si lo haría habitualmente al usar `Debug.WriteLine()` o `console.log()`. Además, la sintaxis de llaves (`{ }`) para generar expresiones también puede ser distinta de la convención para generar valores en el lenguaje de desarrollo que esté usando. (Sin embargo, el contenido dentro de las llaves (`{ }`) de todos modos se debe escribir según la sintaxis del lenguaje de desarrollo).

Si intenta depurar una aplicación activa y busca una característica similar, revise la característica de punto de registro de Snapshot Debugger. Snapshot Debugger es una herramienta que se usa para investigar problemas en aplicaciones de producción. Los puntos de registro también permiten enviar mensajes a la ventana de salida sin tener que modificar el código fuente y sin afectar la aplicación en ejecución. Para más información, consulte [Depuración de aplicaciones activas de Azure](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Escribir mejor código de C# con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Expresiones en el depurador](expressions-in-the-debugger.md)
- [Uso de puntos de interrupción](../debugger/using-breakpoints.md)
- [Depuración de aplicaciones activas de Azure](../debugger/debug-live-azure-applications.md)
