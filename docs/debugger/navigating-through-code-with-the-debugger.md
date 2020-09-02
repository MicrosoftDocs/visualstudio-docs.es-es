---
title: Navegación por el código con el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: how-to
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
ms.openlocfilehash: 5d6b9bb2eb6169de2bbbf41b6d4e96a5960e40fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348254"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navegación por el código con el depurador de Visual Studio

El depurador de Visual Studio puede ayudarle a navegar por el código para inspeccionar el estado de una aplicación y mostrar su flujo de ejecución. Puede usar métodos abreviados de teclado, y depurar comandos, puntos de interrupción y otras características para obtener rápidamente el código que quiera examinar. Familiarizarse con los comandos de navegación y los métodos abreviados de teclado del depurador permite encontrar y resolver problemas de la aplicación de forma más rápida y sencilla.  Si esta es la primera vez que intenta depurar código, le recomendamos que lea [Cómo depurar para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md) y [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de continuar con este artículo.

## <a name="get-into-break-mode"></a>Acceso al "modo de interrupción"

En el *modo de interrupción*, la ejecución de la aplicación se suspende mientras las funciones, las variables y los objetos permanecen en la memoria. Una vez que el depurador está en el modo de interrupción, puede navegar por el código. Las formas más comunes de acceder al modo de interrupción rápidamente son las siguientes:

- Empiece a ejecutar el código paso a paso presionando **F10** o **F11**. Esto le permite encontrar rápidamente el punto de entrada de la aplicación. Después, puede seguir presionando los comandos de paso para navegar por el código.

- [Realice la ejecución hasta una ubicación o función específica](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), por ejemplo, [estableciendo un punto de interrupción](using-breakpoints.md) e iniciando la aplicación.

   Por ejemplo, en el editor de código de Visual Studio, puede usar el comando **Ejecutar hasta el cursor** para iniciar la aplicación, con el depurador asociado, entrar en el modo de interrupción y, a continuación, presionar **F11** para navegar por el código.

   ![Ejecución hasta el cursor y depuración del código paso a paso por instrucciones](../debugger/media/navigate-code-code-stepping.gif "Ejecución hasta el cursor y depuración del código paso a paso por instrucciones")

Una vez en el modo de interrupción, puede usar diversos comandos para navegar por el código. En el modo de interrupción, puede examinar los valores de las variables para buscar infracciones o errores. Para algunos tipos de proyectos, también puede realizar ajustes en la aplicación mientras está en el modo de interrupción.

La mayoría de las ventanas del depurador, como los **módulos** y las ventanas **Inspección**, solo están disponibles mientras el depurador está asociado a la aplicación. Algunas características del depurador, como la presentación de los valores de las variables en la ventana **Variables locales** o la evaluación de las expresiones en la ventana **Inspección**, solo están disponibles mientras el depurador está en pausa (es decir, en el modo de interrupción).

> [!NOTE]
> Si interrumpe código que no tiene archivos de código fuente o de símbolos ( *.pdb*) cargados, el depurador mostrará una página con el mensaje **No se encontraron archivos de código fuente** o **No se encontraron símbolos** que le permitirá encontrar y cargar los archivos. Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen). Si no puede cargar los archivos de código fuente o de símbolos, aún puede depurar las instrucciones de ensamblado en la ventana **Desensamblado**.

## <a name="step-through-code"></a>Examinar el código

Los comandos de paso del depurador le ayudan a inspeccionar el estado de la aplicación o a obtener más información sobre su flujo de ejecución.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Depuración de código paso a paso por instrucciones línea a línea

Para detenerse en cada instrucción durante la depuración, use **Depurar** > **Depurar paso a paso por instrucciones** o presione **F11**.

El depurador recorre paso a paso las instrucciones del código y no las líneas físicas. Por ejemplo, una cláusula `if` se puede escribir en una línea:

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

Sin embargo, cuando esta línea se ejecuta paso a paso por instrucciones, el depurador trata la condición como un paso y el resultado como otro. En el ejemplo anterior, la condición es "true".

En una llamada a una función anidada, **Paso a paso por instrucciones** llega hasta la función más profundamente anidada. Por ejemplo, si utiliza **Paso a paso por instrucciones** en una llamada como `Func1(Func2())`, el depurador ejecuta paso a paso las instrucciones de la función `Func2`.

>[!TIP]
>A medida que se ejecuta cada línea de código, puede mantener el puntero sobre las variables para ver sus valores o usar las [variables locales](autos-and-locals-windows.md) y las ventanas [Inspección](watch-and-quickwatch-windows.md) para ver los valores que cambian. También puede realizar un seguimiento visual de la [pila de llamadas](how-to-use-the-call-stack-window.md) mientras se depuran paso a paso las funciones. (Para Visual Studio Enterprise solamente, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Examen del código y omisión de algunas funciones

Es posible que una función no le interese durante la depuración, o que sepa que funciona, como el código de biblioteca bien probado. Puede usar los siguientes comandos para omitir el código mientras se está ejecutando. Las funciones siguen ejecutándose, pero el depurador las omite.

|Comando de teclado|Comando del menú Depurar|Descripción|
|----------------------|------------------|-----------------|
|**F10**|**Paso a paso por procedimientos**|Si la línea actual contiene una llamada de función, **Paso a paso por procedimientos** ejecuta el código y suspende la ejecución en la primera línea de código después de que se devuelve la función a la que se ha llamado.|
|**Mayús**+**F11**|**Paso a paso para salir**|**Paso a paso para salir** continúa ejecutando el código y suspende la ejecución cuando se devuelve la función actual. El depurador omite la función actual.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Ejecución hasta una ubicación o función determinada

Tal vez prefiera realizar la ejecución directamente en una ubicación o función específica cuando sepa exactamente qué código quiere inspeccionar o sepa dónde quiere iniciar la depuración.

### <a name="run-to-a-breakpoint-in-code"></a>Ejecución en un punto de interrupción en el código

Para establecer un punto de interrupción sencillo en el código, haga clic en el margen izquierdo situado junto a la línea de código donde quiera suspender la ejecución. También puede seleccionar la línea y presionar **F9**, y seleccionar **Depurar** > **Alternar punto de interrupción**, o bien hacer clic con el botón derecho y seleccionar **Punto de interrupción** > **Insertar punto de interrupción**. El punto de interrupción aparece como un punto rojo en el margen izquierdo junto a la línea de código. El depurador suspende la ejecución justo antes de que se ejecute la línea.

![Establecer un punto de interrupción](../debugger/media/dbg_basics_setbreakpoint.png "Establecer un punto de interrupción")

Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Para obtener más información, consulte [Uso de los puntos de interrupción](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Ejecución en un punto de interrupción de función

Puede indicar al depurador que se ejecute hasta que llegue a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.

**Para especificar un punto de interrupción de función por nombre**

1. Seleccione **Depurar** > **Nuevo punto de interrupción** > **Punto de interrupción de función**.

1. En el cuadro de diálogo **Nuevo punto de interrupción de función**, escriba el nombre de la función y seleccione el lenguaje.

   ![Cuadro de diálogo Nuevo punto de interrupción de función](../debugger/media/dbg_execution_newbreakpoint.png "Nuevo punto de interrupción de función")

1. Seleccione **Aceptar**.

Si la función está sobrecargada o en más de un espacio de nombres, puede elegir el que quiera en la ventana **Puntos de interrupción**.

![Puntos de interrupción de función sobrecargados](../debugger/media/dbg_execution_overloadedbreakpoints.png "Puntos de interrupción de función sobrecargados")

**Para seleccionar un punto de interrupción de función de la pila de llamadas**

1. Durante la depuración, abra la ventana **Pila de llamadas**. Para ello, seleccione **Depurar** > **Ventanas** > **Pila de llamadas**.

1. En la ventana **Pila de llamadas**, haga clic con el botón derecho en una función y seleccione **Ejecutar hasta el cursor** o presione **Ctrl**+**F10**.

Para realizar un seguimiento visual de la pila de llamadas, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Ejecución hasta la ubicación del cursor

Para realizar la ejecución hasta la ubicación del cursor, en el código fuente o en la ventana **Pila de llamadas**, seleccione la línea en la que quiera interrumpir la ejecución, haga clic con el botón derecho y seleccione **Ejecutar hasta el cursor** o presione **Ctrl**+**F10**. El hecho de seleccionar **Ejecutar hasta el cursor** es como establecer un punto de interrupción temporal.

### <a name="run-to-click"></a>Icono para ejecutar hasta la línea

Mientras está en pausa en el depurador, puede mantener el puntero sobre una instrucción en el código fuente o en la ventana **Desensamblado** y seleccionar el icono de flecha verde **Ejecutar hasta aquí**. El uso de **Ejecutar hasta clic** elimina la necesidad de establecer un punto de interrupción temporal.

![Ejecutar hasta clic](../debugger/media/dbg-run-to-click.png "Icono para ejecutar hasta la línea")

> [!NOTE]
> **Ejecutar hasta clic** está disponible a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Interrumpir el código manualmente

Para interrumpir en la siguiente línea de código disponible en una aplicación en ejecución, seleccione **Depurar** > **Interrumpir todos** o presione **Ctrl**+**Alt**+**Salto**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Movimiento del puntero para cambiar el flujo de ejecución

Mientras el depurador esté en pausa, una flecha amarilla en el margen de una ventana de código fuente o de la ventana **Desensamblado** indica la ubicación de la siguiente instrucción que se debe ejecutar. Puede cambiar la siguiente instrucción para que se ejecute moviendo esta punta de flecha. Puede omitir una parte del código o volver a una línea anterior. Mover este puntero resulta útil en situaciones como la omisión de una sección de código que contiene un error conocido.

 ![Movimiento del puntero](../debugger/media/dbg_basics_example3.gif "Movimiento del puntero")

Para cambiar la siguiente instrucción para ejecutarse, el depurador debe estar en el modo de interrupción. En el código fuente o la ventana **Desensamblado**, arrastre la punta de flecha amarilla a otra línea o haga clic con el botón derecho en la línea que quiera ejecutar a continuación y seleccione **Establecer instrucción siguiente**.

El contador del programa salta directamente a la nueva ubicación y no se ejecutan las instrucciones entre los puntos de ejecución anteriores y los nuevos. Sin embargo, si mueve el punto de ejecución hacia atrás, no se deshacen las instrucciones intermedias.

>[!CAUTION]
>- Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación.
>- En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.
>- En C++ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.
>- Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando ocurra, aparecerá un mensaje de error que indica que no se puede realizar la operación.
>- En código administrado, no puede mover la instrucción siguiente si:
>   - La instrucción siguiente está en un método diferente de la instrucción actual.
>   - La depuración se inició mediante la depuración Just-In-Time.
>   - Un desenredo de la pila de llamadas está en curso.
>   - Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a> Depuración de código que no es de usuario

De forma predeterminada, el depurador intenta depurar solo el código de la aplicación habilitando un valor llamado *Solo mi código*. Para obtener más información sobre cómo funciona esta característica para los diferentes tipos de proyecto y lenguajes, y cómo puede personalizarla, consulte [Solo mi código](../debugger/just-my-code.md).

Para ver el código del marco, el código de la biblioteca de terceros o las llamadas del sistema durante la depuración, puede deshabilitar Solo mi código. En **Herramientas** (o **Depurar**) > **Opciones** > **Depuración**, desactive la casilla **Habilitar Solo mi código**. Cuando Solo mi código está deshabilitado, el código que no es de usuario aparece en las ventanas del depurador, y este puede depurar el código que no es de usuario paso a paso por instrucciones.

> [!NOTE]
> Sólo mi código no se admite para los proyectos de dispositivos.

### <a name="debug-system-code"></a>Depuración de código del sistema

Si ha cargado símbolos de depuración para el código del sistema de Microsoft y ha deshabilitado Solo mi código, puede ir a una llamada del sistema al igual que lo haría con cualquier otra llamada.

Para cargar símbolos de Microsoft, vea [Configurar ubicaciones de símbolos y las opciones de carga](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Para cargar los símbolos de un componente del sistema específico:**

1. Mientras realiza la depuración, abra la ventana **Módulos**; para ello, seleccione **Depurar** > **Ventanas** > **Módulos** o presione **Ctrl**+**Alt**+**U**.

1. En la ventana **Módulos**, puede indicar qué módulos tienen cargados los símbolos en la columna **Estado del símbolo**. Haga clic con el botón derecho en el módulo para el que quiera cargar los símbolos y seleccione **Cargar símbolos**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para que el depurador vaya a las propiedades y los operadores, elija **Depurar** > **Opciones**. En la página **Depuración** > **General**, desactive la casilla **Saltar propiedades y operadores (solo administrado)** .

## <a name="see-also"></a>Vea también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
