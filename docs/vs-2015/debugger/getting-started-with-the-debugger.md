---
title: Introducción con el depurador | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202307"
---
# <a name="getting-started-with-the-debugger"></a>Introducción al depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador de Visual Studio es fácil de usar en cualquier lenguaje. Aquí le mostraremos cómo depurar un programa sencillo de C#, aunque puede aplicar los mismos pasos para programar en otros lenguajes, como C++ y JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Depurar un proyecto de C# básico  
 Comencemos con una sencilla aplicación de consola de C# (**archivo/nuevo/proyecto**, seleccione **Visual C#** y, a continuación, seleccione **aplicación de consola**). Si no ha trabajado nunca con Visual Studio, consulte [Tutorial: crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). El método **Main** solo agrega 1 a una variable de tipo entero 10 veces y imprime el resultado en la consola:  
  
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
  
 Compile este código en la configuración de **depuración** . Esta configuración se establece de forma predeterminada. Para obtener más información acerca de las configuraciones, vea Descripción de las [configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Ejecute este código en el depurador haciendo clic en depurar **/iniciar depuración** (o en **iniciar** en la barra de herramientas o en **F5**). La aplicación se cierra casi de inmediato, por lo que en realidad no puede saber si se imprime algo en la ventana de consola.  
  
 Puede detener la ejecución el tiempo suficiente para ver la ventana de consola estableciendo un punto de interrupción y ejecutando después paso a paso. Para establecer un punto de interrupción, coloque el cursor en la `Console.WriteLine` línea y haga clic en **depurar/nuevo punto de interrupción o punto de interrupción de función**, o simplemente haga clic en el margen izquierdo en la misma línea. El punto de interrupción debe tener un aspecto similar a este:  
  
 ![Establecer un punto de interrupción](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obtener más información sobre los puntos de interrupción, vea [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Inspeccionar variables  
 La depuración a menudo implica buscar variables que no contengan los valores esperados en un punto determinado. Le mostraremos algunas de las formas en las que puede inspeccionar las variables.  
  
 Vuelva a comenzar la depuración. La ejecución se detiene antes de que se ejecute el código de `Console.WriteLine`. Puede hacer que se ejecute paso a paso por instrucciones (haga clic en **depurar/paso a paso por procedimientos** o **F10**). En este caso, podría haber elegido **Step into** (**F11**) y obtenido el mismo resultado. Explicaremos la diferencia más adelante. La línea con la última llave de apertura del método debería aparecer ahora amarilla. Mire la ventana de la consola. Debería ver **10**.  
  
 Puede mantener el mouse sobre la variable **testInt** para ver el valor actual en una sugerencia de datos.  
  
 ![&#95;conceptos básicos de DBG&#95;&#95;de datos](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Justo debajo de la ventana de código debería ver las ventanas **automático**, **variables locales**e **inspección** . Estas ventanas muestran los valores actuales de las variables en tiempo de ejecución. Las ventanas **automático** y **variables locales** muestran **testInt** con un valor de **10**.  
  
 ![Ventana de Automático al depurar](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obtener más información acerca de estas ventanas, consulte [ventanas automáticas y variables locales](../debugger/autos-and-locals-windows.md).  
  
 Veamos cómo cambia el valor de la variable a medida que avanza el programa. Establezca un punto de interrupción en la `testInt += 1;` línea y reinicie la depuración. Debería ver que **testInt** en las ventanas **variables locales** y **automático** es **0**, e **i** es **1**. Al continuar la depuración (**depurar/continuar**o **continuar** en la barra de herramientas, o **F5**), puede ver que el valor de **testInt** cambia a **1**, después a **2**, etc. Cuando esté cansado de examinar estos cambios, quite el punto de interrupción (**depurar/alternar punto de interrupción**o haga clic en él en el margen) y continúe con la depuración. Si desea quitar todos los puntos de interrupción, haga clic en **depurar/eliminar todos los puntos de interrupción**o **Ctrl + Mayús + F9**y haga clic en **sí** en el cuadro de diálogo que le pregunta **si desea quitar todos los puntos de interrupción?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Llamadas de función Paso a paso por instrucciones y Paso a paso por procedimientos  
 Puede ejecutar código en el depurador instrucción by-Statement (**paso a paso**por instrucciones) o puede ejecutar código mientras el depurador omite las funciones (**paso a paso por procedimientos**) para obtener acceso rápidamente al código en el que está más interesado (el código de función todavía se ejecuta). Puede cambiar entre ambos métodos en la misma sesión de depuración.  
  
 Para ver la diferencia entre **paso a paso por instrucciones** y **paso a paso por procedimientos**, es necesario agregar un método al que llama otro método. Agregue un método a la aplicación de C# y llámelo desde el método Principal. El código debería tener este aspecto:  
  
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
  
 Establezca un punto de interrupción en la llamada `Method1();` del método Principal e inicie la depuración. Cuando se interrumpa la ejecución, haga clic en **depurar/paso a paso** por instrucciones (o **paso a paso por instrucciones** en la barra de herramientas o **F11**). La ejecución vuelve a interrumpirse en la primera llave de Method1():  
  
 ![Ejecutar paso a paso el código](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Detenga la depuración y vuelva a empezar y, cuando la ejecución se interrumpa en el punto de interrupción, haga clic en **depurar/paso a paso por procedimientos** (o **paso a paso por procedimientos** en la barra de herramientas o **F10**) La ejecución se interrumpe nuevamente en `Console.WriteLine("end");`.  
  
 Si desea obtener más información sobre cómo navegar por el código con el depurador, vea [desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).
