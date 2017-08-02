---
title: "Introducci&#243;n al depurador | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introducci&#243;n al depurador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El depurador de Visual Studio es fácil de usar en cualquier lenguaje.  Aquí le mostraremos cómo depurar un programa sencillo de C\#, aunque puede aplicar los mismos pasos para codificar en otros lenguajes, como C\+\+ y JavaScript.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Depurar un proyecto básico de C\#  
 Comencemos con una aplicación de consola sencilla en C\# \(**Archivo \/ Nuevo \/ Proyecto**; luego, seleccione **Visual C\#** y **Aplicación de consola**\).  Si nunca ha trabajado con Visual Studio, consulte [Tutorial: Crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  El método Principal simplemente suma 1 a una variable entera 10 veces e imprime el resultado en la consola:  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i < 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compile este código en la configuración **Depurador**.  Esta configuración se establece de forma predeterminada.  Para obtener más información sobre configuraciones, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Ejecute este código en el depurador haciendo clic en **Depurar \/ Iniciar depuración** \(o **Iniciar** en la barra de herramientas, o F5\).  La aplicación se cierra casi de inmediato, por lo que en realidad no puede saber si se imprime algo en la ventana de consola.  
  
 Puede detener la ejecución el tiempo suficiente para ver la ventana de consola estableciendo un punto de interrupción y ejecutando después paso a paso.  Para establecer un punto de interrupción, coloque el cursor en la línea `Console.WriteLine` y haga clic en **Depurar \/ Nuevo punto de interrupción \/ Punto de interrupción de función**, o bien haga clic en el margen izquierdo en la misma línea.  El punto de interrupción debe tener un aspecto similar a este:  
  
 ![Establecer un punto de interrupción](~/docs/debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obtener más información sobre puntos de interrupción, consulte [Usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
 Vuelva a comenzar la depuración.  La ejecución se detiene antes de que se ejecute el código de `Console.WriteLine`.  Puede hacer que se ejecute hacia adelante \(haga clic en **Depurar \/ Paso a paso por procedimientos**  o **F10**\).  En este caso podría haber elegido **Paso a paso por instrucciones** \(**F11**\) para obtener el mismo resultado; explicaremos la diferencia más adelante.  La línea con la última llave de apertura del método debería aparecer ahora amarilla.  Mire la ventana de la consola.  Debería ver **10**.  Detener la depuración \(**Depurar \/ Detener depuración**, o **Detener depuración** en la barra de herramientas, o **MAYÚS\+F5**\).  
  
 Ahora veamos los valores de las variables.  Justo debajo de la ventana de código debería ver las ventanas **Automático**, **Locales** e **Inspección**.  Estas ventanas muestran los valores actuales de las variables en tiempo de ejecución.  Las ventanas **Automático** y **Locales** muestran testInt con un valor de **10**.  
  
 ![Ventana de Automático al depurar](~/docs/debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obtener más información sobre las ventanas **Automático** y **Locales**, vea [Ventanas de variables](../Topic/Variable%20Windows.md).  
  
 Veamos cómo cambia el valor de la variable a medida que avanza el programa.  Establezca un punto de interrupción en la línea `testInt += 1;` e inicie la depuración.  Debería ver que **testInt** en las ventanas **Locales** y **Automático** es **0**, e **i** es **1**.  Al continuar la depuración \(**Depurar \/ Continuar**, o **Continuar** en la barra de herramientas, o **F5**\), puede ver que el valor de testInt cambia a **1**, luego a **2**, y así sucesivamente.  Cuando se canse de mirar estos cambios, quite el punto de interrupción \(**Depurar \/ Alternar punto de interrupción**, o haga clic en él en el margen\) y continúe la depuración.  Si quiere quitar todos los puntos de interrupción, haga clic en **Depurar \/ Eliminar todos los puntos de interrupción**, o presione **CTRL \+ MAYÚS \+ F9**, y haga clic en **Sí** en el cuadro de diálogo que pregunta **¿Desea quitar todos los puntos de interrupción?**  
  
## Llamadas de función Paso a paso por instrucciones y Paso a paso por procedimientos  
 Para ver la diferencia entre **Paso a paso por instrucciones** y **Paso a paso por procedimientos**, hay que agregar un método al que se llama con otro método.  Agregue un método a la aplicación de C\# y llámelo desde el método Principal.  El código debería tener este aspecto:  
  
```c#  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Establezca un punto de interrupción en la llamada `Method1();` del método Principal e inicie la depuración.  Cuando la ejecución se interrumpa, haga clic en **Depurar \/ Paso a paso por instrucciones** \(o **Paso a paso por instrucciones** en la barra de herramientas, o **F11**\).  La ejecución vuelve a interrumpirse en la primera llave de Method1\(\):  
  
 ![Depurar paso a paso el código](~/docs/debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Detenga la depuración e iníciela de nuevo y, cuando la ejecución se detenga en el punto de interrupción, haga clic en **Depurar \/ Paso a paso por procedimientos**  \(o **Paso a paso por procedimientos** en la barra de herramientas, o **F10**\).  La ejecución se interrumpe nuevamente en `Console.WriteLine("end");`.  
  
 Si quiere más información sobre cómo desplazarse por el código con el depurador, vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).