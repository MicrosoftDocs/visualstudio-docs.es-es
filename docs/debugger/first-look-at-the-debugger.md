---
title: Empezar a trabajar con el depurador de Visual Studio | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a969a75a7c0cda89d040b8829fc8313974646c07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Empezar a trabajar con el depurador de Visual Studio
El depurador de Visual Studio es fácil de usar en cualquier lenguaje. Aquí le mostraremos cómo depurar un programa sencillo de C#, pero puede aplicar los mismos pasos para codificar en otros lenguajes, como C++ y JavaScript.

Para ver un vídeo que muestra características similares, vea [introducción con el depurador](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a>Depurar un proyecto básico de C#  
 Puede empezar con una sencilla aplicación de consola de C# (**archivo > Nuevo > proyecto**, a continuación, seleccione **Visual C#** y, a continuación, **aplicación de consola**). Si nunca ha trabajado con Visual Studio antes, consulte [Tutorial: crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). El **Main** método simplemente suma 1 a una variable entera 10 veces e imprime el resultado en la consola:  
  
```CSharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compile este código en el **depurar** configuración. Esta configuración se establece de forma predeterminada. Para obtener más información acerca de las configuraciones, vea [descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Ejecute este código en el depurador haciendo clic en **Depurar > Iniciar depuración** (o **iniciar** en la barra de herramientas o **F5**). La aplicación se cierra casi de inmediato, por lo que realmente no se puede saber si se imprime algo en la ventana de consola.  
  
 Puede detener la ejecución el tiempo suficiente para ver la ventana de consola estableciendo un punto de interrupción y ejecutando después paso a paso. Para establecer un punto de interrupción, coloque el cursor en el `Console.WriteLine` de línea y haga clic en **Depurar > nuevo punto de interrupción > punto de interrupción de función**, o bien haga clic en el margen izquierdo en la misma línea. El punto de interrupción debe tener un aspecto similar a este:  
  
 ![Establecer un punto de interrupción](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obtener más información acerca de los puntos de interrupción, consulte [utilizar puntos de interrupción](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a>Inspeccionar Variables  
 Depurar a menudo hay que buscar las variables que no contienen los valores que espera en un momento determinado. Le mostraremos algunas de las formas que puede inspeccionar las variables.  
  
 Vuelva a comenzar la depuración. La ejecución se detiene antes de que se ejecute el código de `Console.WriteLine`. Puede hacer que se ejecute hacia adelante (haga clic en **Depurar > paso a paso por** o **F10**). En este caso podría haber elegido **paso a paso** (**F11**) y obtener el mismo resultado; explicaremos la diferencia más adelante. La línea con la última llave de apertura del método debería aparecer ahora amarilla. Mire la ventana de la consola. Debería ver **10**.  
  
 Puede mantener el mouse sobre la **testInt** variable para ver el valor actual en una sugerencia de datos.  
  
 ![DBG &#95; Conceptos básicos de &#95; datos &#95; Sugerencias](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 Justo debajo de la ventana de código debería ver el **automático**, **locales**, y **inspección** windows. Estas ventanas muestran los valores actuales de las variables en tiempo de ejecución. Tanto el **automático** y **variables locales** windows mostrar **testInt** con un valor de **10**.  
  
 ![Ventana de automático al depurar](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obtener más información acerca de estas ventanas, vea [ventanas automático y variables locales](../debugger/autos-and-locals-windows.md).  
  
 Veamos cómo se cambia el valor de la variable tal y como le guiará a través del programa. Establecer un punto de interrupción en el `testInt += 1;` de línea y reinicie la depuración. Debería ver que **testInt** en el **locales** y **automático** windows es **0**, y **i** es **1**. Al continuar la depuración (**Depurar > continuar**, o **continuar** en la barra de herramientas o **F5**), puede ver que el valor de **testInt** cambia a **1**, a continuación, **2**, y así sucesivamente. Cuando se canse de mirar estos cambios, quite el punto de interrupción (**Depurar > Alternar puntos de interrupción**, o haga clic en él en el margen) y continúe la depuración. Si desea quitar todos los puntos de interrupción, haga clic en **Depurar > eliminar todos los puntos de interrupción**, o **CTRL + MAYÚS + F9**y haga clic en **Sí** en el cuadro de diálogo que pregunta **hacer ¿desea quitar todos los puntos de interrupción?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Llamadas de función Paso a paso por instrucciones y Paso a paso por procedimientos  
 Puede ejecutar código en el depurador instrucción (**paso a paso**) o puede ejecutar código mientras el depurador omite las funciones (**paso a paso por**) para obtener acceso rápidamente a código que está más interesado en () código de la función todavía se ejecuta). Puede cambiar entre ambos métodos en la misma sesión de depuración.  
  
 Para ver la diferencia entre **paso a paso** y **paso a paso por**, tenemos que agregar un método que llama a otro método. Agregue un método a la aplicación de C# y llámelo desde el método Principal. El código debería tener este aspecto:  
  
```CSharp  
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
  
 Establezca un punto de interrupción en la llamada `Method1();` del método Principal e inicie la depuración. Cuando se interrumpe la ejecución, haga clic en **Depurar > Depurar paso a paso** (o **paso a paso** en la barra de herramientas o **F11**). La ejecución vuelve a interrumpirse en la primera llave de Method1():  
  
 ![Ejecución paso a paso en código](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Detener la depuración y volver a iniciar y cuando la ejecución se interrumpe en el punto de interrupción, haga clic en **Depurar > paso a paso por** (o **paso a paso por** en la barra de herramientas o **F10**). La ejecución se interrumpe nuevamente en `Console.WriteLine("end");`.  
  
 Si desea obtener más información acerca de cómo navegar por el código con el depurador, consulte [desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).