---
title: "Tutorial: Usar el depurador con m&#233;todos asincr&#243;nicos | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "async (característica), usar el depurador"
  - "await (operador), usar el depurador"
  - "Paso a paso por instrucciones (comando), en operador await"
  - "Paso a paso para salir (comando), en método async"
  - "Paso a paso por procedimientos (comando), en operador await"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Tutorial: Usar el depurador con m&#233;todos asincr&#243;nicos
Mediante la característica Async, se puede llamar a métodos asincrónicos sin definir continuaciones ni dividir el código en varios métodos o expresiones lambda.  Para convertir código sincrónico en asincrónico, se llama a un método asincrónico en lugar de un método sincrónico y se agregan algunas palabras clave al código.  Para obtener más información, vea [Programación asincrónica con Async y Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 En el depurador de Visual Studio, puede utilizar los comandos **Paso a paso por instrucciones**, **Paso a paso por procedimientos** y **Paso a paso para salir** con la característica `Async`.  También puede seguir utilizando puntos de interrupción, sobre todo para ver el flujo de control en una instrucción que contenga un operador await.  En este tutorial, se realizarán las siguientes tareas, que se pueden ejecutar en cualquier orden.  
  
-   Mostrar el flujo de control en una instrucción await mediante puntos de interrupción.  
  
-   Comprender el comportamiento de los comandos **Paso a paso por instrucciones** y **Paso a paso por procedimientos** en instrucciones que contienen un operador await.  
  
-   Comprender el comportamiento del comando **Paso a paso para salir** cuando se utiliza dentro de un método asincrónico.  
  
## Puntos de interrupción para mostrar el flujo de control  
 Si marca un método con el modificador [Async](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) o [async](/dotnet/csharp/language-reference/keywords/async) \(C\#\), puede utilizar el operador [Await](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) o [await](/dotnet/csharp/language-reference/keywords/await) \(C\#\) en el método.  Para crear una expresión await, debe asociar el operador await a una tarea.  Si se llama a una expresión await para la tarea, el método actual finaliza inmediatamente y devuelve una tarea diferente.  Cuando finaliza la tarea que está asociada al operador await, la ejecución se reanuda en el mismo método.  Para obtener más información, vea [Flujo de control en programas Async](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  Un método asincrónico vuelve al llamador cuando encuentra el primer objeto esperado que aún no se ha completado o cuando llega al final del método asincrónico, lo que ocurra primero.  
  
> [!NOTE]
>  Las aplicaciones de consola de estos ejemplos utilizan el método <xref:System.Threading.Tasks.Task.Wait%2A> para impedir que la aplicación finalice en `Main`.  No se debe utilizar el método <xref:System.Threading.Tasks.Task.Wait%2A> fuera de las aplicaciones de consola porque podría producirse una situación de interbloqueo.  
  
 En el ejemplo siguiente se establecen puntos de interrupción para mostrar qué ocurre cuando la aplicación llega a una instrucción await.  También puede mostrar el flujo de control agregando instrucciones `Debug.WriteLine`.  
  
1.  Cree una aplicación de consola y, a continuación, pegue en ella el siguiente código:  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  Establezca puntos de interrupción de depuración en las tres líneas que finalizan con un comentario "set breakpoint" \(establecer punto de interrupción\).  
  
3.  Elija la tecla F5, o elija **Depurar**, **Iniciar depuración** en la barra de menús para ejecutar la aplicación.  
  
     La aplicación entra en el método `ProcessAsync` y se interrumpe en la línea que contiene el operador await.  
  
4.  Elija la tecla F5 de nuevo.  
  
     Dado que la aplicación se ha detenido en una instrucción que contiene un operador await, la aplicación sale inmediatamente del método asincrónico y devuelve una tarea.  Por lo tanto, la aplicación finaliza el método `ProcessAsync` y se interrumpe en el punto de interrupción del método de llamada \(`Main`\).  
  
5.  Elija la tecla F5 de nuevo.  
  
     Cuando se completa el método `DoSomethingAsync`, el código se reanuda después de la instrucción await en el método de llamada.  Por consiguiente, la aplicación se interrumpe en el punto de interrupción en el método `ProcessAsync`.  
  
     Cuando se esperó inicialmente `DoSomethingAsync`, el método `ProcessAsync` finalizó y devolvió una tarea.  Cuando se completó el método `DoSomethingAsync` esperado, la evaluación de la instrucción await generó el valor devuelto de `DoSomethingAsync`.  El método `DoSomethingAsync` se define para que devuelva un valor `Task (Of Integer)` en Visual Basic o `Task<int>` en C\#, por lo que el valor de su instrucción return es un entero.  Para obtener más información, vea [Tipos de valor devueltos de Async](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Obtener y después esperar una tarea  
 En el método `ProcessAsync`, la instrucción `Dim result = Await DoSomethingAsync()` \(Visual Basic\) o `var result = await DoSomethingAsync();` \(C\#\) es una contracción de las dos instrucciones siguientes:  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 La primera línea de código llama al método asincrónico y devuelve una tarea.  Dicha tarea se asocia al operador await en la siguiente línea de código.  La instrucción await finaliza el método \(`ProcessAsync`\) y devuelve una tarea diferente.  Cuando finaliza la tarea que está asociada al operador await, el código se reanuda en el método \(`ProcessAsync`\) después de la instrucción await.  
  
 Cuando la instrucción await devuelve inmediatamente una tarea diferente, dicha tarea es el argumento devuelto del método asincrónico que contiene el operador await \(`ProcessAsync`\).  La tarea devuelta por la instrucción await incluye la ejecución de código que se produce después de la instrucción await en el mismo método. Este es el motivo por el que dicha tarea sea diferente a la tarea que está asociada a la instrucción await.  
  
## Comandos Paso a paso por instrucciones y Paso a paso por procedimientos  
 El comando **Paso a paso por instrucciones** ejecuta paso a paso un método, pero el comando **Paso a paso por procedimientos** ejecuta la llamada al método y, a continuación, se interrumpe en la línea siguiente del método de llamada.  Para obtener más información, vea [Ejecutar el código paso a paso por instrucciones, por procedimientos o para salir](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code).  
  
 El siguiente procedimiento muestra lo que ocurre cuando elige los comandos **Paso a paso por instrucciones** o **Paso a paso por procedimientos** en una instrucción await.  
  
1.  Reemplace el código de la aplicación de consola por el código siguiente.  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  Elija la tecla F11, o elija **Depurar**, **Paso a paso por instrucciones** en la barra de menús para iniciar una demostración del comando `Step Into` en una instrucción que contiene un operador await.  
  
     La aplicación se inicia y se interrumpe en la primera línea, que es `Sub Main()` en Visual Basic o la llave de apertura del método `Main` en C\#.  
  
3.  Elija la tecla F11 tres veces más.  
  
     La aplicación ahora debe estar en la instrucción await del método `ProcessAsync`.  
  
4.  Elija la tecla F11.  
  
     La aplicación entra en el método `DoSomethingAsync` y se interrumpe en la primera línea.  Este comportamiento se produce incluso si, en la instrucción `await`, la aplicación vuelve inmediatamente al método de llamada \(`Main`\).  
  
5.  Siga presionando la tecla F11 hasta que la aplicación vuelva a la instrucción await del método `ProcessAsync`.  
  
6.  Elija la tecla F11.  
  
     La aplicación se interrumpe en la línea que sigue a la instrucción await.  
  
7.  En la barra de menú, elija **Depurar**, **Detener depuración** para detener la ejecución de la aplicación.  
  
     Los pasos siguientes muestran el comando **Paso a paso por procedimientos** en una instrucción await.  
  
8.  Elija la tecla F11 cuatro veces, o elija **Depurar**, **Paso a paso por instrucciones** en la barra de menús cuatro veces.  
  
     La aplicación ahora debe estar en la instrucción await del método `ProcessAsync`.  
  
9. Elija la tecla F10, o elija **Depurar**, **Paso a paso por procedimientos** en la barra de menús.  
  
     La ejecución se interrumpe en la línea que sigue a la instrucción await.  Este comportamiento se produce incluso si la aplicación vuelve inmediatamente al método de llamada \(`Main`\) en la instrucción await.  El comando `Step Over` también depura paso a paso la ejecución del método `DoSomethingAsync`, tal como se espera.  
  
10. En la barra de menú, elija **Depurar**, **Detener depuración** para detener la ejecución de la aplicación.  
  
     Como muestran los pasos siguientes, el comportamiento de los comandos **Paso a paso por instrucciones** y **Paso a paso por procedimientos** difiere ligeramente cuando el operador await se encuentra en una línea diferente de la llamada al método asincrónico.  
  
11. En el método `ProcessAsync`, reemplace la instrucción await por el siguiente código.  La instrucción await original es una contracción de las dos instrucciones siguientes.  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. Elija la tecla F11 o elija **Depurar**, **Paso a paso por instrucciones** varias veces en la barra de menús para iniciar la ejecución y recorrer el código paso a paso.  
  
     En la llamada a `DoSomethingAsync`, el comando **Paso a paso por instrucciones** interrumpe el método `DoSomethingAsync`, mientras que el comando **Paso a paso por procedimientos** va a la siguiente instrucción, según lo previsto.  En la instrucción await, ambos comandos se interrumpen en la instrucción que sigue a la instrucción await.  
  
## Paso a paso para salir  
 En los métodos que no son asincrónicos, el comando **Paso a paso para salir** interrumpe el método de llamada en el código que sigue a la llamada al método.  Para los métodos asincrónicos, la lógica de dónde se interrumpe la ejecución en el método de llamada es más compleja, y dicha lógica depende de si el comando **Paso a paso para salir** se encuentra en la primera línea del método asincrónico.  
  
1.  Reemplace el código de la aplicación de consola por el código siguiente.  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  Establezca un punto de interrupción en la línea `Debug.WriteLine("before")` del método `DoSomethingAsync`.  
  
     Así se muestra el comportamiento del comando **Paso a paso para salir** desde una línea de un método asincrónico que no sea la primera línea.  
  
3.  Elija la tecla F5 o elija **Depurar**, **Iniciar depuración** en la barra de menús para iniciar la aplicación.  
  
     El código se interrumpe en `Debug.WriteLine("before")` en el método `DoSomethingAsync`.  
  
4.  Elija las teclas Mayús\+F11, o elija **Depurar**, **Paso a paso para salir** en la barra de menús.  
  
     La aplicación interrumpe el método de llamada en la instrucción await de la tarea que está asociada al método actual.  Por tanto, la aplicación se interrumpe en la instrucción await del método `ProcessAsync`.  La aplicación no se interrumpe en `Dim z = 0` \(Visual Basic\) o en `int z = 0;` \(C\#\), que es el código que sigue la llamada al método `DoSomethingAsync`.  
  
5.  Elija **Depurar**, **Detener depuración** en la barra de menús para detener la ejecución de la aplicación.  
  
     Los pasos siguientes muestran lo que sucede cuando se aplica el comando **Paso a paso para salir** desde la primera línea de un método asincrónico.  
  
6.  Quite el punto de interrupción existente, y agregue un punto de interrupción en la primera línea del método `DoSomethingAsync`.  
  
     En C\#, agregue el punto de interrupción en la llave de apertura del método `DoSomethingAsync`.  En Visual Basic, agregue el punto de interrupción en la línea que contiene `Async Function DoSomethingAsync() As Task(Of Integer)`.  
  
7.  Elija la tecla F5 para iniciar la aplicación.  
  
     El código se interrumpe en la primera línea del método `DoSomethingAsync`.  
  
8.  En la barra de menús, elija **Depurar**, **Ventanas**, **Salida**.  
  
     Se abre la ventana **Resultados**.  
  
9. Elija las teclas Mayús\+F11, o elija **Depurar**, **Paso a paso para salir** en la barra de menús.  
  
     La aplicación se reanuda hasta que el método asincrónico alcanza su primera instrucción await y, a continuación, la aplicación se interrumpe en la instrucción de llamada.  En consecuencia, la aplicación se interrumpe en `Dim the Task = DoSomethingAsync()` \(Visual Basic\) o `var theTask = DoSomethingAsync();` \(C\#\).  El mensaje "before" ha aparecido en la ventana de salida, pero el mensaje "after" no ha aparecido todavía.  
  
10. Elija la tecla F5 para continuar la ejecución de la aplicación.  
  
     La aplicación continúa con la instrucción que sigue a la instrucción await en la función asincrónica llamada \(`DoSomethingAsync`\).  El mensaje "after" aparece en la ventana de salida.  
  
## Vea también  
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)