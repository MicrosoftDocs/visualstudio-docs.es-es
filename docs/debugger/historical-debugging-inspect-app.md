---
title: Inspección de la aplicación con depuración histórica | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efabc8cd185daed4f018e3e4209e391b5bc39f44
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350451"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Inspección de la aplicación con depuración histórica de IntelliTrace en Visual Studio (C#, Visual Basic, C++)

Puede usar la [depuración histórica](../debugger/historical-debugging.md) para desplazarse hacia atrás y hacia delante por la ejecución de la aplicación e inspeccionar su estado.

Puede usar IntelliTrace en Visual Studio Enterprise, pero no en las ediciones Professional o Community.

## <a name="navigate-your-code-with-historical-debugging"></a>Desplazamiento por el código con depuración histórica

Comencemos con un sencillo programa que tiene un error. En una aplicación de consola C#, agregue el código siguiente:

```csharp
static void Main(string[] args)
{
    int testInt = 0;
    int resultInt = AddAll(testInt);
    Console.WriteLine(resultInt);
}
private static int AddAll(int j)
{
    for (int i = 0; i < 20; i++)
    {
        j = AddInt(j);
    }
    return j;
}

private static int AddInt(int add)
{
    if (add == 10)
    {
        return add += 25;
    }
    return ++add;
}
```

Supondremos que el valor esperado de `resultInt` después de llamar a `AddAll()` es 20 (el resultado de incrementar `testInt` 20 veces). (También supondremos que no puede ver el error en `AddInt()`). Pero el resultado es en realidad 44. ¿Cómo podemos encontrar el error sin pasar por `AddAll()` 10 veces? Podemos usar Depuración histórica para encontrar el error de forma más rápida y sencilla. Esta es la manera de hacerlo:

1. En **Herramientas > Opciones > IntelliTrace > General**, asegúrese de que IntelliTrace está habilitado y seleccione **Eventos e información de llamadas de IntelliTrace**. Si no selecciona esta opción, no podrá ver el medianil de navegación (tal y como se explica más adelante).

2. Establezca un punto de interrupción en la línea `Console.WriteLine(resultInt);` .

3. Inicie la depuración. El código se ejecuta hasta el punto de interrupción. En la ventana **Locales** puede ver que el valor de `resultInt` es 44.

4. Abra la ventana **Herramientas de diagnóstico** (**Depurar > Mostrar herramientas de diagnóstico**). La ventana de código debe ser similar a la que se muestra a continuación:

    ![Ventana de código en el punto de interrupción](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Debería ver una flecha doble junto al margen izquierdo, justo encima del punto de interrupción. Esta área se denomina medianil de navegación y se utiliza para Depuración histórica. Haga clic en la flecha.

    En la ventana de código, debería ver que la línea de código anterior (`int resultInt = AddIterative(testInt);`) es de color rosa. Encima de la ventana verá un mensaje que indica que ya está en Depuración histórica.

    La ventana de código ahora tiene el siguiente aspecto:

    ![Ventana de código en modo de depuración histórica](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Ahora puede depurar paso a paso por instrucciones el método `AddAll()` (**F11**, o el botón **Depurar paso a paso por instrucciones** en el medianil de navegación. Avanzar paso a paso (**F10** o **Ir a llamada siguiente** en el medianil de navegación. La línea rosa se encuentra ahora en la línea `j = AddInt(j);`. En este caso, **F10** no avanza a la siguiente línea de código. sino a la siguiente llamada de función. Depuración histórica va de una llamada a otra y omite las líneas de código que no incluyen una llamada de función.

7. Ahora, depure paso a paso por instrucciones el método `AddInt()`. Debería ver el error en este código inmediatamente.

## <a name="next-steps"></a>Pasos siguientes

Este procedimiento no ha hecho sino arañar la superficie de lo que se puede hacer con Depuración histórica.

- Para ver instantáneas durante la depuración, consulte [Inspección de los estados de aplicación anteriores mediante IntelliTrace](../debugger/view-historical-application-state.md).
- Para obtener más información sobre las distintas configuraciones y los efectos de los botones diferentes en el medianil de navegación, consulte [Características de IntelliTrace](../debugger/intellitrace-features.md).
