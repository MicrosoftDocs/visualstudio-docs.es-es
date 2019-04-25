---
title: Getting Started with the Debugger | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109529"
---
# <a name="getting-started-with-the-debugger"></a>Introducción al depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador de Visual Studio es fácil de usar en cualquier lenguaje. Aquí le mostraremos cómo depurar un programa sencillo de C#, aunque puede aplicar los mismos pasos para programar en otros lenguajes, como C++ y JavaScript.  
  
## <a name="BKMK_Start_debugging_a_VS_project"></a> Depurar un proyecto básicas en C#  
 Comencemos con una sencilla aplicación de consola de C# (**archivo / nuevo / proyecto**, a continuación, seleccione **Visual C#** y, a continuación, seleccione **aplicación de consola**). Si nunca ha trabajado con Visual Studio antes, vea [Tutorial: Crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). El **Main** método simplemente suma 1 a una variable entera 10 veces e imprime el resultado en la consola:  
  
```csharp  
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
  
 Ejecute este código en el depurador haciendo **depurar / Iniciar depuración** (o **iniciar** en la barra de herramientas o **F5**). La aplicación se cierra casi de inmediato, por lo que en realidad no puede saber si se imprime algo en la ventana de consola.  
  
 Puede detener la ejecución el tiempo suficiente para ver la ventana de consola estableciendo un punto de interrupción y ejecutando después paso a paso. Para establecer un punto de interrupción, coloque el cursor en el `Console.WriteLine` de línea y haga clic en **depurar / nuevo punto de interrupción / punto de interrupción de función**, o bien haga clic en el margen izquierdo en la misma línea. El punto de interrupción debe tener un aspecto similar a este:  
  
 ![Establezca un punto de interrupción](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obtener más información acerca de los puntos de interrupción, consulte [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
## <a name="BKMK_Inspect_Variables"></a> Inspeccionar Variables  
 La depuración a menudo implica buscar las variables que no contienen los valores que espera en un momento determinado. Le mostraremos algunas de las formas que puede inspeccionar las variables.  
  
 Vuelva a comenzar la depuración. La ejecución se detiene antes de que se ejecute el código de `Console.WriteLine`. Puede hacer que se ejecute hacia adelante (haga clic en **depurar / paso Over** o **F10**). En este caso podría haber elegido **paso a paso** (**F11**) y obtener el mismo resultado; explicaremos la diferencia más adelante. La línea con la última llave de apertura del método debería aparecer ahora amarilla. Mire la ventana de la consola. Debería ver **10**.  
  
 Puede mantener el puntero sobre el **testInt** variable para ver el valor actual en una sugerencia de datos.  
  
 ![DBG&#95;Fundamentos&#95;datos&#95;sugerencias](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Justo debajo de la ventana de código debería ver el **automático**, **variables locales**, y **inspección** windows. Estas ventanas muestran los valores actuales de las variables en tiempo de ejecución. Tanto el **automático** y **variables locales** mostrar windows **testInt** con un valor de **10**.  
  
 ![Ventana de automático al depurar](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obtener más información sobre estas ventanas, vea [automático y variables locales Windows](../debugger/autos-and-locals-windows.md).  
  
 Veamos cómo cambia el valor de la variable a medida que avanza el programa. Establecer un punto de interrupción en el `testInt += 1;` de línea y reinicie la depuración. Debería ver que **testInt** en el **locales** y **automático** windows es **0**, y **i** es **1**. Al continuar la depuración (**depurar / continuar**, o **continuar** en la barra de herramientas o **F5**), puede ver que el valor de **testInt** cambia a **1**, a continuación, **2**, y así sucesivamente. Cuando se canse de mirar estos cambios, quite el punto de interrupción (**depurar / Alternar punto de interrupción**, o haga clic en él en el margen) y continuar con la depuración. Si desea quitar todos los puntos de interrupción, haga clic en **depurar / eliminar todos los puntos de interrupción**, o **CTRL + MAYÚS + F9**y haga clic en **Sí** en el cuadro de diálogo que pregunta **entonces ¿desea quitar todos los puntos de interrupción?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Llamadas de función Paso a paso por instrucciones y Paso a paso por procedimientos  
 Puede ejecutar código en el depurador instrucción (**paso a paso**) o puede ejecutar código mientras el depurador omite las funciones (**saltar**) para ponerse rápidamente al código que está más interesado en () código de función se ejecuta). Puede cambiar entre ambos métodos en la misma sesión de depuración.  
  
 Para ver la diferencia entre **paso a paso** y **saltar**, necesitamos agregar un método que llama a otro método. Agregue un método a la aplicación de C# y llámelo desde el método Principal. El código debería tener este aspecto:  
  
```csharp  
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
  
 Establezca un punto de interrupción en la llamada `Method1();` del método Principal e inicie la depuración. Cuando la ejecución se interrumpa, haga clic en **depurar / paso a paso** (o **paso a paso** en la barra de herramientas o **F11**). La ejecución vuelve a interrumpirse en la primera llave de Method1():  
  
 ![Ejecución paso a paso en código](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Detener la depuración y vuelva a iniciar y, cuando la ejecución se interrumpe en el punto de interrupción, haga clic en **depurar / paso Over** (o **saltar** en la barra de herramientas o **F10**). La ejecución se interrumpe nuevamente en `Console.WriteLine("end");`.  
  
 Si desea obtener más información sobre la navegación por código con el depurador, vea [desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).
