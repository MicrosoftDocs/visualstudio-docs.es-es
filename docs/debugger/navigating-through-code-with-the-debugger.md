---
title: Navegar por el código con el depurador . Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301096"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navegue por el código con el depurador de Visual Studio

El depurador de Visual Studio puede ayudarle a navegar por el código para inspeccionar el estado de una aplicación y mostrar su flujo de ejecución. Puede usar métodos abreviados de teclado, comandos de depuración, puntos de interrupción y otras características para obtener rápidamente el código que desea examinar. La familiaridad con los comandos de navegación del depurador y los accesos directos hace que sea más rápido y fácil encontrar y resolver problemas de la aplicación.  Si es la primera vez que intenta depurar código, es posible que desee leer [Depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [técnicas y herramientas](../debugger/write-better-code-with-visual-studio.md) de depuración antes de pasar por este artículo.

## <a name="get-into-break-mode"></a>Entrar en "modo de interrupción"

En el modo de *interrupción,* la ejecución de la aplicación se suspende mientras las funciones, variables y objetos permanecen en la memoria. Una vez que el depurador está en modo de interrupción, puede navegar por el código. Las formas más comunes de entrar en el modo de interrupción rápidamente es:

- Comience el paso del código presionando **F10** o **F11**. Esto le permite encontrar rápidamente el punto de entrada de la aplicación y, a continuación, puede seguir presionando los comandos de paso para navegar por el código.

- [Ejecutar a una ubicación o función específica,](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)por ejemplo, [estableciendo un punto](using-breakpoints.md) de interrupción e iniciando la aplicación.

   Por ejemplo, desde el editor de código de Visual Studio, puede usar el comando **Ejecutar en cursor** para iniciar la aplicación, el depurador adjunto y entrar en modo de interrupción y, a continuación, **F11** para navegar por el código.

   ![Ejecutar al cursor y entrar en el código](../debugger/media/navigate-code-code-stepping.gif "Ejecutar al cursor y entrar en el código")

Una vez en el modo de interrupción, puede usar una variedad de comandos para navegar por el código. Mientras está en modo de interrupción, puede examinar los valores de las variables para buscar infracciones o errores. Para algunos tipos de proyecto, también puede realizar ajustes en la aplicación mientras está en modo de interrupción.

La mayoría de las ventanas del depurador, como las **ventanas Módulos** y **Inspección,** solo están disponibles mientras el depurador está asociado a la aplicación. Algunas características del depurador, como ver valores de variables en la ventana **Locales** o evaluar expresiones en la ventana **Inspección,** solo están disponibles mientras el depurador está en pausa (es decir, en modo de interrupción).

> [!NOTE]
> Si divide en código que no tiene archivos de origen o símbolo (*.pdb*) cargados, el depurador muestra una página Archivos de origen **no encontrados** o **Símbolos no encontrados** que pueden ayudarle a encontrar y cargar los archivos. Consulte [Especificar símbolo (.pdb) y archivos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)de origen . Si no puede cargar el símbolo o los archivos de origen, todavía puede depurar las instrucciones de ensamblado en la ventana **Desensamblado.**

## <a name="step-through-code"></a>Examinar el código

Los comandos de paso del depurador le ayudan a inspeccionar el estado de la aplicación u obtener más información sobre su flujo de ejecución.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Entra en código línea por línea

Para detener cada instrucción durante la depuración, use **Depurar** > **paso a**, o presione **F11**.

El depurador recorre instrucciones de código, no líneas físicas. Por ejemplo, una cláusula `if` se puede escribir en una línea:

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Sin embargo, cuando entra en esta línea, el depurador trata la condición como un paso y la consecuencia como otra. En el ejemplo anterior, la condición es true.

En una llamada a una función anidada, **Paso a paso por instrucciones** llega hasta la función más profundamente anidada. Por ejemplo, si utiliza **Step** Into `Func1(Func2())`en una llamada `Func2`como , el depurador pasa a la función .

>[!TIP]
>Al ejecutar cada línea de código, puede pasar el cursor sobre las variables para ver sus valores o usar las [ventanas Locales](autos-and-locals-windows.md) y [Inspección](watch-and-quickwatch-windows.md) para ver cómo cambian los valores. También puede realizar un seguimiento visual de la pila de [llamadas](how-to-use-the-call-stack-window.md) mientras entra en funciones. (Solo para Visual Studio Enterprise, vea Asignar métodos en la pila de llamadas durante la [depuración).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Paso a través del código y omitir algunas funciones

Es posible que no le importe una función durante la depuración, o que sepa que funciona, como el código de biblioteca bien probado. Puede usar los siguientes comandos para omitir el código mientras se pisa el código. Las funciones siguen ejecutándose, pero el depurador las omite.

|Comando teclado|Comando del menú Depurar|Descripción|
|----------------------|------------------|-----------------|
|**F10**|**Paso a paso por procedimientos**|Si la línea actual contiene una llamada de función, **Step Over** ejecuta el código y, a continuación, suspende la ejecución en la primera línea de código después de que se devuelve la función llamada.|
|**Shift**+**F11**|**Step Out**|**Step Out** continúa ejecutando código y suspende la ejecución cuando se devuelve la función actual. El depurador omite la función actual.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Ejecutar a una ubicación o función específica

Es posible que prefiera ejecutar directamente a una ubicación o función específica cuando sepa exactamente qué código desea inspeccionar, o saber dónde desea iniciar la depuración.

### <a name="run-to-a-breakpoint-in-code"></a>Ejecutar a un punto de interrupción en el código

Para establecer un punto de interrupción simple en el código, haga clic en el margen izquierdo situado junto a la línea de código donde desea suspender la ejecución. También puede seleccionar la línea y presionar **F9**, seleccionar **Depurar** > alternar punto de**interrupción**o **hacer** > clic con el botón derecho y seleccionar Punto de interrupción Insertar punto de**interrupción**. El punto de interrupción aparece como un punto rojo en el margen izquierdo junto a la línea de código. El depurador suspende la ejecución justo antes de que se ejecute la línea.

![Establecer un punto de interrupción](../debugger/media/dbg_basics_setbreakpoint.png "Establecer un punto de interrupción")

Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Para obtener más información, consulte [Uso de puntos](../debugger/using-breakpoints.md)de interrupción .

### <a name="run-to-a-function-breakpoint"></a>Ejecutar a un punto de interrupción de función

Puede indicar al depurador que se ejecute hasta que llegue a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.

**Para especificar un punto de interrupción de función por nombre**

1. Seleccione **Depurar** > nuevo punto de**interrupción de la función** de punto de**interrupción** > 

1. En el cuadro de diálogo Nuevo punto de interrupción de **función,** escriba el nombre de la función y seleccione su idioma.

   ![Cuadro de diálogo Nuevo punto de interrupción de función](../debugger/media/dbg_execution_newbreakpoint.png "Nuevo punto de interrupción de la función")

1. Seleccione **Aceptar**.

Si la función está sobrecargada o en más de un espacio de nombres, puede elegir el que desee en la ventana **Puntos** de interrupción.

![Puntos de interrupción de funciones sobrecargados](../debugger/media/dbg_execution_overloadedbreakpoints.png "Puntos de interrupción de funciones sobrecargados")

**Para seleccionar un punto de interrupción de función de la pila de llamadas**

1. Durante la depuración, abra la ventana **Pila** de llamadas seleccionando **Depurar** > **pila de llamadas**de**Windows** > .

1. En la ventana Pila de **llamadas,** haga clic con el botón derecho en una función y seleccione **Ejecutar al cursor**o presione **Ctrl**+**F10**.

Para realizar un seguimiento visual de la pila de llamadas, consulte Asignar métodos en la pila de llamadas durante la [depuración.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="run-to-a-cursor-location"></a>Ejecutar a una ubicación de cursor

Para ejecutar en la ubicación del cursor, en el código fuente o en la ventana **Pila** de llamadas, seleccione la línea en la que desea romper, haga clic con el botón derecho y seleccione **Ejecutar al cursor**o presione **Ctrl**+**F10**. Seleccionar **Ejecutar al cursor** es como establecer un punto de interrupción temporal.

### <a name="run-to-click"></a>Icono para ejecutar hasta la línea

Mientras está en pausa en el depurador, puede pasar el cursor sobre una instrucción en el código fuente o en la ventana **Desensamblado** y seleccionar el icono **Ejecutar ejecución hasta aquí** flecha verde. El uso de **Ejecutar para hacer clic** elimina la necesidad de establecer un punto de interrupción temporal.

![Ejecutar hasta clic](../debugger/media/dbg-run-to-click.png "Icono para ejecutar hasta la línea")

> [!NOTE]
> **Ejecutar a clic** está [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]disponible a partir de .

### <a name="manually-break-into-code"></a>Interrumpir el código manualmente

Para interrumpir la siguiente línea de código disponible en una aplicación en ejecución, seleccione **Depurar** > **interrumpir todo**o presione **Ctrl**+**Alt**+**Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Mueva el puntero para cambiar el flujo de ejecución

Mientras el depurador está en pausa, una punta de flecha amarilla en el margen del código fuente o la ventana **Desensamblado** marca la ubicación de la siguiente instrucción que se va a ejecutar. Puede cambiar la siguiente instrucción para ejecutar moviendo esta punta de flecha. Puede omitir una parte del código o volver a una línea anterior. Mover el puntero es útil para situaciones como omitir una sección de código que contiene un error conocido.

 ![Mover el puntero](../debugger/media/dbg_basics_example3.gif "Mover el puntero")

Para cambiar la siguiente instrucción que se va a ejecutar, el depurador debe estar en modo de interrupción. En el código fuente o en la ventana **Desensamblado,** arrastre la punta de flecha amarilla a una línea diferente o haga clic con el botón derecho en la línea que desea ejecutar a continuación y seleccione **Establecer instrucción siguiente**.

El contador del programa salta directamente a la nueva ubicación y las instrucciones entre los puntos de ejecución antiguos y nuevos no se ejecutan. Sin embargo, si mueve el punto de ejecución hacia atrás, las instrucciones que intervienen no se deshacen.

>[!CAUTION]
>- Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación.
>- En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.
>- En C++ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.
>- Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando esto sucede, un mensaje de error le indica que la operación no es compatible.
>- En el código administrado, no puede mover la siguiente instrucción si:
>   - La instrucción siguiente está en un método diferente de la instrucción actual.
>   - La depuración se inició mediante la depuración Just-In-Time.
>   - Una pila de llamadas desenredado está en curso.
>   - Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Depurar código que no sea de usuario

De forma predeterminada, el depurador intenta depurar solo el código de la aplicación habilitando una configuración denominada *Solo mi código*. Para obtener más información sobre cómo funciona esta característica para diferentes tipos de proyectos e idiomas, y cómo puede personalizarla, consulte [Solo mi código](../debugger/just-my-code.md).

Para examinar el código del marco de trabajo, el código de biblioteca de terceros o las llamadas del sistema durante la depuración, puede deshabilitar Solo mi código. En **Herramientas** (o **Depurar**) >**depuración** **de opciones** > , desactive la casilla **Habilitar solo mi código.** Cuando Just My Code está deshabilitado, el código que no es de usuario aparece en las ventanas del depurador y el depurador puede entrar en el código que no es de usuario.

> [!NOTE]
> Sólo mi código no se admite para los proyectos de dispositivos.

### <a name="debug-system-code"></a>Depurar código del sistema

Si ha cargado símbolos de depuración para el código del sistema de Microsoft y ha deshabilitado Solo mi código, puede entrar en una llamada del sistema del igual que cualquier otra llamada.

Para cargar símbolos de Microsoft, consulte Configurar ubicaciones de [símbolos y opciones](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)de carga .

**Para cargar símbolos para un componente de sistema específico:**

1. Mientras está depurando, abra la ventana **Módulos** seleccionando **Depurar** > **módulos**de**Windows** > o presionando **Ctrl**+**Alt**+**U**.

1. En la ventana **Módulos,** puede saber qué módulos tienen símbolos cargados en la columna Estado del **símbolo.** Haga clic con el botón derecho en el módulo para el que desea cargar símbolos y seleccione **Cargar símbolos**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para habilitar el paso a paso en propiedades u operadores, elija**Opciones** **de depuración** > . En la página**General** **de depuración,** > desactive la casilla De paso sobre propiedades **y operadores (solo administrado).**

## <a name="see-also"></a>Consulte también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primero mire la depuración](../debugger/debugger-feature-tour.md)
