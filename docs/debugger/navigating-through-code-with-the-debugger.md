---
title: "Desplazarse por el c&#243;digo con el depurador | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.execution"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "depurar [Visual Studio], control de ejecución"
  - "ejecución, control en el depurador"
  - "ejecutar instrucciones paso a paso"
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 42
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Desplazarse por el c&#243;digo con el depurador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay muchas maneras de desplazarse por el código en el depurador: recorrer o depurar paso a paso por instrucciones los métodos, ejecutar hasta un punto de interrupción o una ubicación especificada, y especificar si se desea restringir la depuración al código propio o incluir símbolos para depurar código externo.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Ejecutar el código paso a paso por instrucciones, por procedimientos o para salir  
 Uno de los procedimientos de depuración más comunes es la *ejecución paso a paso*. En este procedimiento, se ejecuta el código línea por línea. Cuando se detiene la ejecución, por ejemplo, cuando se ejecuta el depurador hasta un punto de interrupción, puede usar tres comandos del menú **Depurar** para recorrer el código paso a paso:  
  
|Comando de menú|Método abreviado de teclado|Descripción|  
|---------------------|---------------------------------|-----------------|  
|**Paso a paso por instrucciones**|**F11**|Si la línea contiene una llamada a una función, **Paso a paso por instrucciones** sólo ejecuta la llamada en sí y, a continuación, se detiene en la primera línea de código incluida en la función. En caso contrario, **Paso a paso por instrucciones** ejecuta la siguiente instrucción.|  
|**Paso a paso por procedimientos**|**F10**|Si la línea contiene una llamada a una función, **Paso a paso por procedimientos** ejecuta la función llamada y, a continuación, se detiene en la primera línea de código incluida en la función de llamada. En caso contrario, **Paso a paso por instrucciones** ejecuta la siguiente instrucción.|  
|**Paso a paso para salir**|**Shift\+F11**|**Paso a paso para salir** reanuda la ejecución del código hasta que regresa la función y, a continuación, se interrumpe en el punto devuelto de la función de llamada.|  
  
-   En una llamada a una función anidada, **Paso a paso por instrucciones** llega hasta la función más profundamente anidada. Si utiliza **Paso a paso por instrucciones** en una llamada como `Func1(Func2())`, el depurador ejecuta paso a paso las instrucciones de la función `Func2`.  
  
-   El depurador recorre paso a paso las instrucciones del código en lugar de las líneas físicas. Por ejemplo, una cláusula `if` se puede escribir en una línea:  
  
    ```c#  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integet = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Cuando esta línea se ejecuta paso a paso por instrucciones, el depurador trata la condición como un paso y el resultado como otro \(en este ejemplo, la condición es true\).  
  
 Para realizar un seguimiento visual de la pila de llamadas mientras se depuran paso a paso las funciones, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Interrumpir el código mediante puntos de interrupción o Interrumpir todos  
 Cuando se depura una aplicación con el depurador de VS, la aplicación se está ejecutando o está en modo de interrupción.  
  
 El depurador interrumpe la ejecución de la aplicación cuando llega a un punto de interrupción o cuando se produce una excepción. También puede interrumpir manualmente la ejecución en cualquier momento.  
  
 Un punto de interrupción es una señal que indica al depurador que debe suspender temporalmente la ejecución de la aplicación en un punto determinado. Cuando la ejecución se suspende en un punto de interrupción, se dice que el programa se encuentra en modo de interrupción. Entrar en el modo de interrupción no detiene ni finaliza la ejecución del programa, cuya ejecución se puede reanudar en cualquier momento.  
  
 La mayoría de las características del depurador, como la presentación de los valores de las variables en la ventana Variables locales o la evaluación de las expresiones en la ventana Inspección, solo están disponibles en el modo de interrupción. Todos los elementos de la aplicación permanecen en la memoria \(por ejemplo, las funciones, variables y objetos\), pero se suspenden sus movimientos y actividades. Durante el modo de interrupción, puede examinar las posiciones de los elementos y estados para buscar infracciones o errores. También puede realizar ajustes en la aplicación mientras está en modo de interrupción.  
  
 Por último, puede configurar puntos de interrupción para suspender la ejecución en función de una serie de condiciones. Vea [Usar puntos de interrupción](../debugger/using-breakpoints.md). En esta sección se explican dos maneras básicas de interrumpir la ejecución del código.  
  
1.  **Establecer puntos de interrupción en el código**  
  
     Para establecer un punto de interrupción simple en el código, abra el archivo de código fuente en el editor de Visual Studio. Establezca el cursor en la línea de código en la que desea interrumpir y elija **Punto de interrupción**, **Insertar punto de interrupción** en el menú contextual \(teclado: **F9**\). El depurador interrumpe la ejecución inmediatamente antes de que se ejecute la línea.  
  
     ![Establecer un punto de interrupción](../debugger/media/dbg_basics_setbreakpoint.png "DBG\_Basics\_SetBreakpoint")  
  
     Los puntos de interrupción proporcionan un amplio conjunto de funcionalidades adicionales en Visual Studio, como los puntos de interrupción condicionales y de seguimiento. Vea [Usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
2.  **Interrumpir el código manualmente**  
  
     Para interrumpir en la siguiente línea de código disponible de una aplicación en ejecución, elija **Depurar**, **Interrumpir todos** \(teclado: **Ctrl\+Alt\+Break**\).  
  
-   Si está depurando con la opción Solo mi código habilitada, se interrumpe en la siguiente línea de código del proyecto. Vea [Restringir la ejecución paso a paso a Solo mi código](#BKMK_Restrict_stepping_to_Just_My_Code).  
  
-   Si depura varios programas, un punto de interrupción o el comando Interrumpir todos afecta de forma predeterminada a todos los programas que se están depurando. Vea [Configurar el comportamiento de ejecución de varios procesos](../debugger/debug-multiple-processes.md#BKMK_Configure_the_execution_behavior_of_multiple_processes).  
  
-   Si interrumpe el código mientras se está ejecutando sin los archivos de código fuente o de símbolos \(archivos .pdb\) correspondientes, el depurador mostrará una página con el mensaje **No se encontraron archivos de código fuente** o **No se encontraron símbolos** que le permitirá encontrar los archivos adecuados. Vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
     Si no puede obtener acceso a los archivos de compatibilidad, aún puede depurar las instrucciones de ensamblado en la ventana Desensamblado.  
  
##  <a name="BKMK_Run_to_a_specified_location_or_function"></a> Ejecutar hasta una ubicación o función determinada  
 En algunas ocasiones, puede que desee ejecutar el código hasta un punto determinado y después detener la ejecución. Si ha establecido un punto de interrupción en la ubicación en la que desea interrumpir, elija **Depurar**, **Iniciar depuración** si no ha iniciado la depuración, o **Depurar**, **Continuar**. \(En ambos casos **F5** es la tecla de método abreviado\). El depurador se detiene en el punto de interrupción siguiente en la ejecución del código. Elija **Depurar**, **Continuar** hasta que llegue al punto de interrupción que desea.  
  
 También puede ejecutar hasta el punto donde haya colocado el cursor en el editor de código o hasta una función específica.  
  
 **Ejecutar un proceso hasta la ubicación del cursor**  
  
 Para ejecutar un proceso hasta la ubicación del cursor, coloque el cursor en una línea de código ejecutable de una ventana de código fuente. En el menú contextual del editor, elija **Ejecutar hasta el cursor**.  
  
 **Ejecutar un proceso hasta una función de la pila de llamadas**  
  
 En la ventana **Pila de llamadas**, seleccione la función y elija **Ejecutar hasta el cursor** en el menú contextual. Para realizar un seguimiento visual de la pila de llamadas, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
 **Ejecutar un proceso hasta una función especificada por nombre**  
  
 Puede indicar al depurador que ejecute la aplicación hasta que llegue a una función especificada. Puede especificar la función por su nombre o elegirla en la pila de llamadas.  
  
 Para especificar una función por su nombre, elija **Depurar**, **Nuevo punto de interrupción**, **Interrumpir en función** y escriba el nombre de la función y otra información de identificación.  
  
 ![Cuadro de diálogo Nuevo punto de interrupción](../debugger/media/dbg_execution_newbreakpoint.png "DBG\_Execution\_NewBreakpoint")  
  
 Si la función se sobrecarga o está en varios espacios de nombres, puede elegir las funciones que desee en el cuadro de diálogo **Elegir puntos de interrupción**.  
  
 ![Cuadro de diálogo Elegir puntos de interrupción](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG\_Execution\_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Establecer la siguiente instrucción que se debe ejecutar  
 Después de interrumpir el depurador, puede mover el punto de ejecución para establecer la siguiente instrucción de código que se debe ejecutar. Una flecha amarilla en el margen de una ventana de código fuente o de la ventana Desensamblado indica la ubicación de la siguiente instrucción que se debe ejecutar. Moviendo esta flecha, puede saltarse una parte del código o volver a una línea previamente ejecutada. Puede utilizar esto en situaciones como la omisión de una sección de código que contiene un error conocido.  
  
 ![Example2](../debugger/media/dbg_basics_example2.png "DBG\_Basics\_Example2")  
  
 Para establecer la siguiente instrucción que se debe ejecutar, siga uno de estos procedimientos:  
  
-   En una ventana de código fuente, arrastre la flecha amarilla hasta la ubicación en la que desea establecer la siguiente instrucción, dentro del mismo archivo de código fuente.  
  
-   En una ventana de código fuente, establezca el cursor en la línea que desea ejecutar a continuación y elija **Establecer instrucción siguiente** en el menú contextual.  
  
-   En la ventana Desensamblado, establezca el cursor en la instrucción de ensamblado que desea ejecutar a continuación y elija **Establecer instrucción siguiente** en el menú contextual.  
  
> [!CAUTION]
>  Al establecer la siguiente instrucción, el contador del programa salta directamente a la nueva ubicación. Utilice este comando con precaución.  
>   
>  -   No se ejecutan las instrucciones entre los puntos de ejecución anteriores y nuevos.  
> -   Si mueve el punto de ejecución hacia atrás, no se deshacen las instrucciones intermedias.  
> -   Al mover la instrucción siguiente a otro ámbito o función normalmente se producen daños en la pila de llamadas y un error o excepción en tiempo de ejecución. Si intenta mover la instrucción siguiente a otro ámbito, el depurador abre un cuadro de diálogo con una advertencia que le ofrece la oportunidad de cancelar la operación. En Visual Basic, no puede mover la instrucción siguiente a otro ámbito o función.  
> -   En C\+\+ nativo, si ha habilitado comprobaciones en tiempo de ejecución, al establecer la instrucción siguiente se puede producir una excepción cuando la ejecución llegue al final del método.  
> -   Cuando la opción Editar y continuar está habilitada, **Establecer instrucción siguiente** genera un error si se han realizado modificaciones que Editar y continuar no puede reasignar inmediatamente. Esto puede suceder, por ejemplo, si se ha editado código en un bloque catch. Cuando ocurra, aparecerá un mensaje de error que indica que no se puede realizar la operación.  
  
> [!NOTE]
>  En código administrado, no puede mover la instrucción siguiente en las situaciones siguientes:  
>   
>  -   La instrucción siguiente está en un método diferente de la instrucción actual.  
> -   La depuración se inició a través de la depuración Just\-In\-Time.  
> -   Un desenredo de la pila de llamadas está en curso.  
> -   Se ha producido una excepción System.StackOverflowException o System.Threading.ThreadAbortException.  
  
 No se puede establecer la siguiente instrucción mientras se está ejecutando activamente la aplicación. Para establecer la siguiente instrucción, el depurador debe estar en modo de interrupción.  
  
##  <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a> Restringir la ejecución paso a paso a Solo mi código  
 Puede que, durante la depuración, desee examinar únicamente el código que ha escrito y pasar por alto otro código, como el correspondiente a las llamadas al sistema. Puede hacer esto mediante la depuración de Sólo mi código. Sólo mi código oculta el código de no usuario para que no aparezca en las ventanas del depurador. Mientras avanza, el depurador avanza paso a paso a través del código de no usuario, pero no se detiene en él. Vea [Solo mi código](../debugger/just-my-code.md)  
  
> [!NOTE]
>  Sólo mi código no se admite para los proyectos de dispositivos.  
  
##  <a name="BKMK_Step_into_system_calls"></a> Ir a llamadas del sistema  
 Si ha cargado símbolos de depuración para el código del sistema y Solo mi código no está habilitado, puede ir a una llamada del sistema al igual que lo haría con cualquier otra llamada.  
  
 Para acceder a los archivos de símbolos de Microsoft, vea [Usar servidores de símbolos para buscar archivos de símbolos que no estén en el equipo local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) en el tema [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Para cargar los símbolos de un componente del sistema específico durante la depuración:  
  
1.  Abra la ventana Módulos \(teclado: **Ctrl\+Alt\+U**\).  
  
2.  Seleccione el módulo para el que desea cargar los símbolos.  
  
     Puede indicar qué módulos tienen cargados los símbolos examinando la columna **Estado del símbolo**.  
  
3.  Elija **Cargar símbolos** en el menú contextual.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Ir a propiedades y operadores en código administrado  
 El depurador se salta las propiedades y los operadores en código administrado de forma predeterminada. En la mayoría de los casos, esto proporciona una mejor experiencia de depuración. Para que el depurador vaya a las propiedades y los operadores, elija **Depuración**, **Opciones y configuración**. En la página **Depuración**, **General**, desactive la casilla **Saltar propiedades y operadores \(solo administrado\)**.