---
title: Desplazarse por el código con el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88608943"
---
# <a name="navigating-through-code-with-the-debugger"></a>Desplazarse por el código con el depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Familiarícese con los comandos y los métodos abreviados para navegar por el código en el depurador y eso hará que sea más rápido y fácil encontrar y resolver problemas en la aplicación. Mientras navega por el código en el depurador, puede [inspeccionar el estado de la aplicación](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) u obtener más información sobre su flujo de ejecución.  
  
## <a name="start-debugging"></a>Iniciar la depuración  
 A menudo, se inicia una sesión de depuración con **F5** **(depurar**  /  **iniciar**depuración). Este comando inicia la aplicación con el depurador asociado.  
  
 La flecha verde también inicia el depurador (igual que **F5**).  
  
 ![DBG&#95;Basics&#95;iniciar la depuración&#95;](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Algunas otras maneras en que puede iniciar la aplicación con el depurador adjunto incluyen **F11** ([paso a paso por instrucciones](#BKMK_Step_into__over__or_out_of_the_code)),  **F10** ([paso a paso por instrucciones](#BKMK_Step_over_Step_out)) o mediante **ejecutar hasta el cursor**.  Vea las demás secciones de este tema para obtener información sobre lo que hacen estas opciones.  
  
 Al depurar, la línea amarilla muestra el código que se ejecutará a continuación.  
  
 ![Conceptos básicos de&#95;de DBG&#95;modo de&#95;de interrupción](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Durante la depuración, puede cambiar entre comandos como **F5**, **F11** y usar otras características que se describen en este tema (como los puntos de interrupción) para llegar rápidamente al código que desea examinar.  
  
 La mayoría de las características del depurador, como la visualización de valores de variables en la ventana variables locales o la evaluación de expresiones en el ventana Inspección, solo están disponibles mientras el depurador está en pausa (también denominado *modo de interrupción*). Cuando el depurador está en pausa, el estado de la aplicación se suspende mientras las funciones, variables y objetos permanecen en la memoria. En el modo de interrupción, puede examinar los puestos y los Estados de los elementos para buscar infracciones o errores. Para algunos tipos de proyectos, también puede realizar ajustes en la aplicación mientras está en el modo de interrupción.  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Entrar en el código, línea por línea  
 Para detenerse en cada línea de código (cada instrucción) durante la depuración, use el método abreviado de teclado **F11** (o **depurar**  /  **paso a paso** por instrucciones en el menú).  
  
> [!TIP]
> Al ejecutar cada línea de código, puede mantener el mouse sobre las variables para ver sus valores o usar las ventanas [variables locales](../debugger/autos-and-locals-windows.md) e [inspección](../debugger/autos-and-locals-windows.md) para ver sus valores.  
  
 Estos son algunos detalles sobre el comportamiento de **paso a paso por instrucciones**:  
  
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
  
  Para realizar un seguimiento visual de la pila de llamadas durante la ejecución paso a paso de las funciones, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> Desplazarse por el código, omitir funciones  
 Al ejecutar el código en el depurador, a menudo se da cuenta de que no necesita ver lo que ocurre en una función determinada (no le importa o sabe que funciona, como el código de biblioteca bien probado). Use estos comandos para omitir el código (las funciones todavía se ejecutan, por supuesto, pero el depurador los omite).  
  
|Comando de teclado|Comando de menú|Descripción|  
|----------------------|------------------|-----------------|  
|**F10**|**Paso a paso por procedimientos**|Si la línea actual contiene una llamada de función, **paso a paso por procedimientos** ejecuta el código y suspende la ejecución en la primera línea de código después de que se devuelva la función llamada.|  
|**Mayús+F11**|**Depurar paso a paso para salir**|**Paso a paso para salir** continúa ejecutando el código y suspende la ejecución cuando se devuelve la función actual (el depurador omite la función actual).|  
  
> [!TIP]
> Si necesita encontrar el punto de entrada en la aplicación, empiece con **F10** o **F11**. Estos comandos suelen ser útiles cuando se inspecciona el estado de la aplicación o se intenta obtener más información sobre su flujo de ejecución.  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Ejecución hasta una ubicación o función determinada  
 A menudo, el método preferido para depurar código, estos métodos son útiles cuando se sabe exactamente qué código se desea inspeccionar, o al menos sabe dónde desea iniciar la depuración.  
  
- **Establecer puntos de interrupción en el código**  
  
     Para establecer un punto de interrupción simple en el código, abra el archivo de código fuente en el editor de Visual Studio. Establezca el cursor en la línea de código donde desea suspender la ejecución y, a continuación, haga clic con el botón secundario en la ventana de código para ver el menú contextual y elija **punto de interrupción/Insertar punto de interrupción** (o presione **F9**). El depurador suspende la ejecución justo antes de que se ejecute la línea.  
  
     ![Establecer un punto de interrupción](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Vea [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
- **Ejecutar un proceso hasta la ubicación del cursor**  
  
     Para ejecutar un proceso hasta la ubicación del cursor, coloque el cursor en una línea de código ejecutable de una ventana de código fuente. En el menú contextual del editor (haga clic con el botón derecho en el editor), elija **ejecutar hasta el cursor**. Esto es como establecer un punto de interrupción temporal.  
  
- **Interrumpir el código manualmente**  
  
     Para interrumpir en la siguiente línea de código disponible de una aplicación en ejecución, elija **Depurar**, **Interrumpir todos** (teclado: **Ctrl+Alt+Break**).  
  
     Si interrumpe el código mientras se está ejecutando sin los archivos de código fuente o de símbolos (archivos .pdb) correspondientes, el depurador mostrará una página con el mensaje **No se encontraron archivos de código fuente** o **No se encontraron símbolos** que le permitirá encontrar los archivos adecuados. Vea [especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si no puede obtener acceso a los archivos de compatibilidad, aún puede depurar las instrucciones de ensamblado en la ventana Desensamblado.  
  
- **Ejecutar un proceso hasta una función de la pila de llamadas**  
  
     En la ventana **pila de llamadas** (disponible durante la depuración), seleccione la función, haga clic con el botón secundario y elija **ejecutar hasta el cursor**. Para realizar un seguimiento visual de la pila de llamadas, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Ejecutar un proceso hasta una función especificada por nombre**  
  
     Puede indicar al depurador que ejecute la aplicación hasta que llegue a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.  
  
     Para especificar una función por su nombre, elija **Depurar**, **Nuevo punto de interrupción**, **Interrumpir en función**y escriba el nombre de la función y otra información de identificación.  
  
     ![Cuadro de diálogo Nuevo punto de interrupción](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Si la función se sobrecarga o está en varios espacios de nombres, puede elegir las funciones que desee en el cuadro de diálogo **Elegir puntos de interrupción** .  
  
     ![Elegir puntos de interrupción (cuadro de diálogo)](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Movimiento del puntero para cambiar el flujo de ejecución  
 Mientras el depurador está en pausa, puede desplace el puntero de instrucción para establecer la siguiente instrucción de código que se va a ejecutar. Una flecha amarilla en el margen de una ventana de código fuente o de la ventana Desensamblado indica la ubicación de la siguiente instrucción que se debe ejecutar. Moviendo esta flecha, puede saltarse una parte del código o volver a una línea previamente ejecutada. Puede utilizar esto en situaciones como la omisión de una sección de código que contiene un error conocido.  
  
 ![Ejemplo 2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Para establecer la siguiente instrucción que se debe ejecutar, siga uno de estos procedimientos:  
  
- En una ventana de código fuente, arrastre la flecha amarilla hasta la ubicación en la que desea establecer la siguiente instrucción, dentro del mismo archivo de código fuente.  
  
- En una ventana de código fuente, establezca el cursor en la línea que desea ejecutar a continuación, haga clic con el botón secundario y elija **Establecer instrucción siguiente**.  
  
- En la ventana Desensamblado, establezca el cursor en la instrucción de ensamblado que desea ejecutar a continuación, haga clic con el botón secundario en y elija **Establecer instrucción siguiente**.  
  
> [!CAUTION]
> Al establecer la siguiente instrucción, el contador del programa salta directamente a la nueva ubicación. Utilice este comando con precaución.  
> 
> - No se ejecutan las instrucciones entre los puntos de ejecución anteriores y nuevos.  
>   - Si mueve el punto de ejecución hacia atrás, no se deshacen las instrucciones intermedias.  
>   - Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación. En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.  
>   - En C++ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.  
>   - Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando ocurra, aparecerá un mensaje de error que indica que no se puede realizar la operación.  
> 
> [!NOTE]
> En código administrado, no puede mover la instrucción siguiente en las situaciones siguientes:  
> 
> - La instrucción siguiente está en un método diferente de la instrucción actual.  
>   - La depuración se inició a través de la depuración Just-In-Time.  
>   - Un desenredo de la pila de llamadas está en curso.  
>   - Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.  
  
 No se puede establecer la siguiente instrucción mientras se está ejecutando activamente la aplicación. Para establecer la siguiente instrucción, el depurador debe estar en modo de interrupción.  
  
## <a name="step-into-non-user-code"></a>Entrar en código que no es de usuario  
 De forma predeterminada, el depurador intenta mostrar solo el código de la aplicación durante la depuración, que viene determinado por una configuración del depurador llamada *solo mi código*. (Consulte [solo mi código](../debugger/just-my-code.md) para ver cómo funciona para los diferentes tipos de proyecto e idiomas y cómo puede personalizar el comportamiento). Sin embargo, a veces durante la depuración, es posible que desee examinar el código del marco, el código de la biblioteca de terceros o las llamadas al sistema operativo (llamadas del sistema).  
  
 Para desactivar solo mi código, vaya a **herramientas**  /  **Opciones**  /  **depurar** y desactive la casilla **Habilitar solo mi código** .  
  
 Cuando Solo mi código está deshabilitado, el depurador puede entrar en el código que no es de usuario y aparece en las ventanas del depurador.  
  
> [!NOTE]
> Sólo mi código no se admite para los proyectos de dispositivos.  
  
 **Ir a llamadas del sistema**  
  
 Si ha cargado símbolos de depuración para el código del sistema y Solo mi código no está habilitado, puede ir a una llamada del sistema igual que cualquier otra llamada.  
  
 Para obtener acceso a los archivos de símbolos de Microsoft, vea [usar servidores de símbolos para buscar archivos de símbolos que no estén en el equipo local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) en el tema [especificar símbolos (. pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 Para cargar los símbolos de un componente del sistema específico durante la depuración:  
  
1. Abra la ventana Módulos (teclado: **Ctrl+Alt+U**).  
  
2. Seleccione el módulo para el que desea cargar los símbolos.  
  
     Puede indicar qué módulos tienen cargados los símbolos examinando la columna **Estado del símbolo** .  
  
3. Elija **Cargar símbolos** en el menú contextual.  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado  
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para que el depurador vaya a las propiedades y los operadores, elija **Depurar** / **Opciones**. En la página general de **depuración**  /  **General** , desactive la casilla **saltar propiedades y operadores (solo administrado)** .
