---
title: Navegar por el código con el depurador | Microsoft Docs
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
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "70222655"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Desplazarse por el código con el depurador de Visual Studio

El depurador de Visual Studio puede ayudarle a navegar por el código para inspeccionar el estado de una aplicación y mostrar su flujo de ejecución. Puede usar métodos abreviados de teclado, comandos de depuración, puntos de interrupción y otras características para obtener rápidamente el código que desea examinar. Familiarizarse con los comandos de navegación del depurador y los accesos directos permite encontrar y resolver problemas de la aplicación de forma más rápida y sencilla.  Si es la primera vez que intenta depurar código, puede que desee leer la [depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de pasar a este artículo.

## <a name="basic-debugging"></a>Depuración básica

Para iniciar la aplicación con el depurador asociado, presione **F5**, seleccione **depurar**  > **iniciar depuración**o seleccione la flecha verde en la barra de herramientas de Visual Studio.

 ![Conceptos&#95;básicos de&#95;dbg&#95;iniciar depuración](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Mientras realiza la depuración, un resaltado amarillo muestra la línea de código que se ejecutará a continuación.

 ![Modo&#95;de&#95;interrupción&#95;de conceptos básicos de dbg](../debugger/media/dbg_basics_break_mode.png "Modo de interrupción")

La mayoría de las ventanas del depurador, como los **módulos** y las ventanas de **inspección** , solo están disponibles mientras se ejecuta el depurador. Algunas características del depurador, como la visualización de valores de variable en la ventana **variables locales** o la evaluación de expresiones en la ventana **inspección** , solo están disponibles mientras el depurador está en pausa en un punto de interrupción, también denominado *modo de interrupción*.

En el modo de interrupción, la ejecución de la aplicación se suspende mientras las funciones, variables y objetos permanecen en la memoria. Puede examinar las posiciones y los Estados de los elementos para buscar infracciones o errores. En el caso de algunos tipos de proyecto, también puede realizar ajustes en la aplicación mientras está en modo de interrupción. Para ver un vídeo que muestra estas características, consulte [Introducción con el depurador](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Si interrumpe el código que no tiene archivos de código fuente o de símbolos ( *. pdb*) cargados, el depurador muestra la página **archivos de origen no encontrados** o **símbolos no encontrados** , que puede ayudarle a encontrar y cargar los archivos. Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen). Si no puede cargar los archivos de símbolos o de código fuente, todavía puede depurar las instrucciones de ensamblado en la ventana **Desensamblado** .

No siempre tiene que iniciar la depuración iniciando una aplicación al principio. También puede presionar **F11** para depurar [paso a paso por instrucciones en el código](#BKMK_Step_into__over__or_out_of_the_code), presionar **F10** para [desplazarse por el código](#BKMK_Step_over_Step_out)o [ejecutar hasta una ubicación o función específica](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Examinar el código

Los comandos de paso del depurador le ayudan a inspeccionar el estado de la aplicación o a obtener más información sobre su flujo de ejecución.

Si necesita encontrar el punto de entrada en la aplicación, empiece con **F10** o **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Ir al código línea por línea

Para detenerse en cada línea de código o instrucción durante la depuración, use **Debug  >  depurar** **paso a paso**por instrucciones o presione **F11**.

El depurador recorre las instrucciones de código, no las líneas físicas. Por ejemplo, una cláusula `if` se puede escribir en una línea:

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

Sin embargo, al entrar en esta línea, el depurador trata la condición como un paso y la consecuencia como otra. En el ejemplo anterior, la condición es true.

En una llamada a una función anidada, **Paso a paso por instrucciones** llega hasta la función más profundamente anidada. Por ejemplo, si usa **paso a paso por instrucciones** en una llamada como `Func1(Func2())`, el depurador se recorre en el `Func2` de la función.

>[!TIP]
>Al ejecutar cada línea de código, puede mantener el mouse sobre las variables para ver sus valores o usar las ventanas [variables locales](autos-and-locals-windows.md) e [inspección](watch-and-quickwatch-windows.md) para ver los valores cambiados. También puede realizar un seguimiento visual de la pila de llamadas durante la ejecución paso a paso de las funciones. Vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a>Recorrer el código y omitir algunas funciones

Es posible que no le interese una función durante la depuración o sepa que funciona, como el código de biblioteca bien probado. Puede usar los siguientes comandos para omitir el código. Las funciones siguen ejecutándose, pero el depurador las omite.

|Comando de teclado|Comando de menú Depurar|Descripción|
|----------------------|------------------|-----------------|
|**F10**|**Paso a paso por procedimientos**|Si la línea actual contiene una llamada de función, el **paso por procedimientos** ejecuta el código y suspende la ejecución en la primera línea de código después de que se devuelva la función llamada.|
|**Mayús**+**F11**|**Paso a paso para salir**|**Paso a paso para salir** continúa ejecutando el código y suspende la ejecución cuando se devuelve la función actual. El depurador omite la función actual.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Ejecutar hasta una ubicación o función específica

Puede que prefiera ejecutar directamente en una ubicación o función específica cuando sepa exactamente qué código desea inspeccionar o sabe dónde desea iniciar la depuración.

### <a name="run-to-a-breakpoint-in-code"></a>Ejecutar hasta un punto de interrupción en el código

Para establecer un punto de interrupción simple en el código, haga clic en el margen izquierdo situado junto a la línea de código donde desea suspender la ejecución. También puede seleccionar la línea y presionar **F9**, seleccionar **depurar**  > **alternar punto de interrupción**o hacer clic con el botón derecho y seleccionar **punto de interrupción**  > **Insertar punto de interrupción**. El punto de interrupción aparece como un punto rojo en el margen izquierdo junto a la línea de código. El depurador suspende la ejecución justo antes de que se ejecute la línea.

![Establecer un punto de interrupción](../debugger/media/dbg_basics_setbreakpoint.png "Establecer un punto de interrupción")

Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Para obtener más información, vea [usar puntos de interrupción](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Ejecutar hasta un punto de interrupción de función

Puede indicar al depurador que se ejecute hasta que llegue a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.

**Para especificar un punto de interrupción de función por nombre**

1. Seleccione **Depurar**  > **nuevo punto** de interrupción  > **función punto de interrupción**

1. En el cuadro de diálogo **nuevo punto de interrupción de función** , escriba el nombre de la función y seleccione su idioma.

   ![Cuadro de diálogo nuevo punto de interrupción de función](../debugger/media/dbg_execution_newbreakpoint.png "Nuevo punto de interrupción de función")

1. Seleccione **Aceptar**.

Si la función está sobrecargada o en más de un espacio de nombres, puede elegir la que desee en la ventana **puntos de interrupción** .

![Puntos de interrupción de función sobrecargados](../debugger/media/dbg_execution_overloadedbreakpoints.png "Puntos de interrupción de función sobrecargados")

**Para seleccionar un punto de interrupción de función de la pila de llamadas**

1. Durante la depuración, abra la ventana **pila de llamadas** ; para ello, seleccione **depurar**  > **Windows**  > **pila de llamadas**.

1. En la **ventana pila de llamadas** , haga clic con el botón secundario en una función y seleccione **ejecutar hasta el cursor**o presione **Ctrl** +**F10**.

Para realizar un seguimiento visual de la pila de llamadas, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Ejecutar hasta una ubicación del cursor

Para ejecutar hasta la ubicación del cursor, en el código fuente o en la ventana **pila de llamadas** , seleccione la línea en la que desea interrumpir la ejecución, haga clic con el botón secundario y seleccione **ejecutar hasta el cursor**o presione **Ctrl** +**F10**. La selección de **ejecutar hasta el cursor** es como establecer un punto de interrupción temporal.

### <a name="run-to-click"></a>Icono para ejecutar hasta la línea

Mientras está en pausa en el depurador, puede mantener el mouse sobre una instrucción en el código fuente o en la ventana **Desensamblado** y seleccionar el icono de flecha **ejecutar hasta aquí** verde. El uso **de ejecutar hasta clic** elimina la necesidad de establecer un punto de interrupción temporal.

![Ejecutar hasta clic](../debugger/media/dbg-run-to-click.png "Icono para ejecutar hasta la línea")

> [!NOTE]
> **Ejecutar hasta clic** está disponible a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Interrumpir el código manualmente

Para interrumpir en la siguiente línea de código disponible en una aplicación en ejecución, seleccione **Depurar**  > **interrumpir todo**o presione **Ctrl** +**Alt** +**interrumpir**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Mueva el puntero para cambiar el flujo de ejecución

Mientras el depurador está en pausa, una punta de flecha amarilla en el margen de la ventana de código fuente o **Desensamblado** marca la ubicación de la siguiente instrucción que se va a ejecutar. Puede cambiar la siguiente instrucción para que se ejecute moviendo esta punta de flecha. Puede omitir una parte del código o volver a una línea anterior. Mover el puntero es útil en situaciones como la omisión de una sección de código que contiene un error conocido.

 ![Movimiento del puntero](../debugger/media/dbg_basics_example3.gif "Movimiento del puntero")

Para cambiar la siguiente instrucción que se va a ejecutar, el depurador debe estar en modo de interrupción. En la ventana código fuente o **Desensamblado** , arrastre la punta de flecha amarilla a otra línea o haga clic con el botón secundario en la línea que desea ejecutar siguiente y seleccione **Establecer instrucción siguiente**.

El contador del programa salta directamente a la nueva ubicación y no se ejecutan las instrucciones entre los puntos de ejecución anteriores y nuevos. Sin embargo, si mueve el punto de ejecución hacia atrás, no se deshacen las instrucciones intermedias.

>[!CAUTION]
>- Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación.
>- En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.
>- En C++ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.
>- Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando esto sucede, un mensaje de error indica que la operación no se admite.
>- En código administrado, no se puede pasar la siguiente instrucción si:
>   - La instrucción siguiente está en un método diferente de la instrucción actual.
>   - La depuración se inició con la depuración Just-in-Time.
>   - Un desenredo de la pila de llamadas está en curso.
>   - Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Depurar código que no es de usuario

De forma predeterminada, el depurador intenta depurar solo el código de la aplicación habilitando una configuración llamada *solo mi código*. Para obtener más información sobre cómo funciona esta característica para los diferentes tipos de proyecto y lenguajes, y cómo puede personalizarlo, consulte [solo mi código](../debugger/just-my-code.md).

Para ver el código del marco, el código de la biblioteca de terceros o las llamadas del sistema durante la depuración, puede deshabilitar Solo mi código. En **herramientas** (o **depurar**) > **Opciones**  > **depuración**, desactive la casilla **Habilitar solo mi código** . Cuando Solo mi código está deshabilitado, el código que no es de usuario aparece en las ventanas del depurador y el depurador puede entrar en el código que no es de usuario.

> [!NOTE]
> Sólo mi código no se admite para los proyectos de dispositivos.

### <a name="debug-system-code"></a>Depurar código del sistema

Si ha cargado símbolos de depuración para el código del sistema de Microsoft y ha deshabilitado Solo mi código, puede ir a una llamada del sistema igual que cualquier otra llamada.

Para cargar símbolos de Microsoft, vea [configurar las ubicaciones de símbolos y cargar opciones](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Para cargar los símbolos de un componente del sistema específico:**

1. Mientras realiza la depuración, abra la ventana **módulos** seleccionando **depurar**  > **módulos**de  >  de**Windows** o presionando **Ctrl** +**Alt** +**U**.

1. En la ventana **módulos** , puede indicar qué módulos tienen cargados los símbolos en la columna **Estado del símbolo** . Haga clic con el botón secundario en el módulo para el que desea cargar los símbolos y seleccione **cargar símbolos**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para habilitar la ejecución paso a paso de propiedades u operadores, elija **depurar** **Opciones**de  > . En la página **Depuración** > **General**, desactive la casilla **Saltar propiedades y operadores (solo administrado)** .

## <a name="see-also"></a>Vea también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
