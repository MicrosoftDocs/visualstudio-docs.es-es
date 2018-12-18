---
title: Desplazarse por el código con el depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43155bbd4236ea34d67058443e8814f7ccf00b1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750579"
---
# <a name="navigating-through-code-with-the-debugger"></a>Desplazarse por el código con el depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Familiarícese con los comandos y métodos abreviados para navegar por el código en el depurador y que le resultará más rápido y fácil de buscar y resolver problemas de la aplicación. Si bien navegar por el código en el depurador, puede [inspeccionar el estado de la aplicación](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) o Aprenda más sobre su flujo de ejecución.  
  
## <a name="start-debugging"></a>Iniciar depuración  
 A menudo, inicia una sesión de depuración con **F5** (**depurar** / **Iniciar depuración**). Este comando inicia la aplicación con el depurador adjunto.  
  
 La flecha verde también inicia el depurador (igual que **F5**).  
  
 ![DBG&#95;Fundamentos&#95;iniciar&#95;depuración](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Incluyen otras formas de que puede iniciar la aplicación con el depurador adjunto **F11** ([ir a código](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([paso a través de código](#BKMK_Step_over_Step_out)), o mediante uso de **ejecutar hasta el Cursor**.  Vea las otras secciones de este tema para obtener información sobre lo que hacer estas opciones.  
  
 Al depurar, la línea amarilla muestra el código que se ejecutará a continuación.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Durante la depuración, puede alternar entre los comandos como **F5**, **F11** y usar otras características descritas en este tema (por ejemplo, los puntos de interrupción) para ponerse rápidamente al código que desea examinar.  
  
 Mayoría de las características de depurador, como ver los valores de variable en la ventana variables locales o evaluación de expresiones en la ventana Inspección, solo está disponible mientras el depurador está en pausa (también denominada *modo de interrupción*). Cuando el depurador está en pausa, su estado de la aplicación se suspende mientras las funciones, variables, y los objetos permanecen en memoria. Mientras esté en modo de interrupción, puede examinar las posiciones de los elementos y Estados para buscar infracciones o errores. Para algunos tipos de proyecto, también puede realizar ajustes en la aplicación en modo de interrupción.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Ir al código, línea por línea  
 Para detener en cada línea de código (cada instrucción) durante la depuración, use el **F11** método abreviado de teclado (o **depurar** / **paso a paso** en el menú).  
  
> [!TIP]
>  Cuando se ejecuta cada línea de código, puede mantener el puntero sobre las variables para ver sus valores o usar el [variables locales](../debugger/autos-and-locals-windows.md) y [inspección](../debugger/autos-and-locals-windows.md) windows para ver sus valores cambia.  
  
 Estos son algunos detalles sobre el comportamiento de **paso a paso**:  
  
- En una llamada a una función anidada, **Paso a paso por instrucciones** llega hasta la función más profundamente anidada. Si utiliza **Paso a paso por instrucciones** en una llamada como `Func1(Func2())`, el depurador ejecuta paso a paso las instrucciones de la función `Func2`.  
  
- El depurador recorre paso a paso las instrucciones del código en lugar de las líneas físicas. Por ejemplo, una cláusula `if` se puede escribir en una línea:  
  
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
  
   Cuando esta línea se ejecuta paso a paso por instrucciones, el depurador trata la condición como un paso y el resultado como otro (en este ejemplo, la condición es true).  
  
  Para realizar un seguimiento al entrar en las funciones de la pila de llamadas, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Recorrer el código, se omitirá las funciones  
 Al ejecutar código en el depurador, a menudo se dará cuenta que no es necesario ver lo que ocurre en una función concreta (no le interesa lo o sabe funciona, como código de biblioteca totalmente probado). Utilice estos comandos para saltar a través del código (las funciones todavía se ejecutan, por supuesto, pero el depurador omite sobre ellos).  
  
|Comando de teclado|Comando de menú|Descripción|  
|----------------------|------------------|-----------------|  
|**F10**|**Paso a paso por procedimientos**|Si la línea actual contiene una llamada de función, **saltar** ejecuta el código, a continuación, suspende la ejecución en la primera línea de código después de la función llamada.|  
|**Mayús+F11**|**Paso a paso para salir**|**Paso a paso fuera** continúa la ejecución de código y suspende la ejecución (el depurador se salta a través de la función actual) que devuelve la función actual.|  
  
> [!TIP]
>  Si necesita buscar el punto de entrada en la aplicación, comience con **F10** o **F11**. Estos comandos son muy útiles cuando está intentando buscar más información acerca de su flujo de ejecución o inspeccionar el estado de la aplicación.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Ejecutar hasta una ubicación específica o función  
 A menudo el método preferido de depuración de código, estos métodos son útiles cuando se sabe exactamente qué código que desea inspeccionar o al menos se sabe dónde desea iniciar la depuración.  
  
-   **Establecer puntos de interrupción en el código**  
  
     Para establecer un punto de interrupción simple en el código, abra el archivo de código fuente en el editor de Visual Studio. Establezca el cursor en la línea de código donde desea suspender la ejecución y, a continuación, haga clic en la ventana de código para ver el menú contextual y elija **punto de interrupción / Insertar punto de interrupción** (o presione **F9**). El depurador suspende la derecha de la ejecución antes de ejecuta la línea.  
  
     ![Establezca un punto de interrupción](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
-   **Ejecutar un proceso hasta la ubicación del cursor**  
  
     Para ejecutar un proceso hasta la ubicación del cursor, coloque el cursor en una línea de código ejecutable de una ventana de código fuente. En el menú del editor contextual (clic derecho en el editor), elija **ejecutar hasta el Cursor**. Se trata como establecer un punto de interrupción temporal.  
  
-   **Interrumpir el código manualmente**  
  
     Para interrumpir en la siguiente línea de código disponible de una aplicación en ejecución, elija **Depurar**, **Interrumpir todos** (teclado: **Ctrl+Alt+Break**).  
  
     Si interrumpe el código mientras se está ejecutando sin los archivos de código fuente o de símbolos (archivos .pdb) correspondientes, el depurador mostrará una página con el mensaje **No se encontraron archivos de código fuente** o **No se encontraron símbolos** que le permitirá encontrar los archivos adecuados. Consulte [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si no puede obtener acceso a los archivos de compatibilidad, aún puede depurar las instrucciones de ensamblado en la ventana Desensamblado.  
  
-   **Ejecutar un proceso hasta una función de la pila de llamadas**  
  
     En el **pila de llamadas** ventana (disponible durante la depuración), seleccione la función, haga clic en y elija **ejecutar hasta el Cursor**. Para realizar un seguimiento la pila de llamadas, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Ejecutar un proceso hasta una función especificada por nombre**  
  
     Puede indicar al depurador que ejecute la aplicación hasta que llega a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.  
  
     Para especificar una función por su nombre, elija **Depurar**, **Nuevo punto de interrupción**, **Interrumpir en función**y escriba el nombre de la función y otra información de identificación.  
  
     ![Cuadro de diálogo nuevo punto de interrupción](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Si la función se sobrecarga o está en varios espacios de nombres, puede elegir las funciones que desee en el cuadro de diálogo **Elegir puntos de interrupción** .  
  
     ![Elija el cuadro de diálogo de los puntos de interrupción](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Mueva el puntero para cambiar el flujo de ejecución  
 Cuando el depurador está pausado, puede mover el puntero de instrucción para establecer la siguiente instrucción de código que se ejecutará. Una flecha amarilla en el margen de una ventana de código fuente o de la ventana Desensamblado indica la ubicación de la siguiente instrucción que se debe ejecutar. Moviendo esta flecha, puede saltarse una parte del código o volver a una línea previamente ejecutada. Puede utilizar esto en situaciones como la omisión de una sección de código que contiene un error conocido.  
  
 ![Ejemplo2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Para establecer la siguiente instrucción que se debe ejecutar, siga uno de estos procedimientos:  
  
-   En una ventana de código fuente, arrastre la flecha amarilla hasta la ubicación en la que desea establecer la siguiente instrucción, dentro del mismo archivo de código fuente.  
  
-   En una ventana de código fuente, establezca el cursor en la línea que desea ejecutar a continuación, haga clic en y elija **Establecer instrucción siguiente**.  
  
-   En la ventana Desensamblado, establezca el cursor en la instrucción de ensamblado que desea ejecutar a continuación, haga clic en una y elija **Establecer instrucción siguiente**.  
  
> [!CAUTION]
>  Al establecer la siguiente instrucción, el contador del programa salta directamente a la nueva ubicación. Utilice este comando con precaución.  
> 
> - No se ejecutan las instrucciones entre los puntos de ejecución anteriores y nuevos.  
>   -   Si mueve el punto de ejecución hacia atrás, no se deshacen las instrucciones intermedias.  
>   -   Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación. En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.  
>   -   En C++ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.  
>   -   Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando ocurra, aparecerá un mensaje de error que indica que no se puede realizar la operación.  
> 
> [!NOTE]
>  En código administrado, no puede mover la instrucción siguiente en las situaciones siguientes:  
> 
> - La instrucción siguiente está en un método diferente de la instrucción actual.  
>   -   La depuración se inició a través de la depuración Just-In-Time.  
>   -   Un desenredo de la pila de llamadas está en curso.  
>   -   Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.  
  
 No se puede establecer la siguiente instrucción mientras se está ejecutando activamente la aplicación. Para establecer la siguiente instrucción, el depurador debe estar en modo de interrupción.  
  
## <a name="step-into-non-user-code"></a>Ir al código que no es de usuario  
 De forma predeterminada, el depurador intenta mostrar solo el código de aplicación durante la depuración, que viene determinada por un depurador llamada *solo mi código*. (Consulte [solo mi código](../debugger/just-my-code.md) para ver cómo funciona esto para diferentes tipos de proyectos y lenguajes y cómo puede personalizar el comportamiento.) Sin embargo, en ocasiones, durante la depuración, puede mirar el código de framework, código de la biblioteca de terceros o las llamadas al sistema operativo (llamadas del sistema).  
  
 Puede desactivar sólo mi código, vaya a **herramientas** / **opciones** / **depuración** y desactive el **habilitar solo mi código** casilla de verificación.  
  
 Cuando solo mi código está deshabilitada, el depurador puede ir al código que no es de usuario y código de usuario no aparece en las ventanas del depurador.  
  
> [!NOTE]
>  Sólo mi código no se admite para los proyectos de dispositivos.  
  
 **Ir a llamadas del sistema**  
  
 Si ha cargado los símbolos de depuración para código del sistema y no está habilitado solo mi código, puede entrar en una llamada del sistema se puede hacer cualquier otra llamada.  
  
 Para obtener acceso a los archivos de símbolos de Microsoft, consulte [usar servidores de símbolos para buscar archivos de símbolos no en la máquina local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) en el [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tema.  
  
 Para cargar los símbolos de un componente del sistema específico durante la depuración:  
  
1.  Abra la ventana Módulos (teclado: **Ctrl+Alt+U**).  
  
2.  Seleccione el módulo para el que desea cargar los símbolos.  
  
     Puede indicar qué módulos tienen cargados los símbolos examinando la columna **Estado del símbolo** .  
  
3.  Elija **Cargar símbolos** en el menú contextual.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado  
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para habilitar la ejecución paso a paso en las propiedades o los operadores, elija **depurar** / **opciones**. En la página **Depuración** / **General** , desactive la casilla **Saltar propiedades y operadores (solo administrado)** .





