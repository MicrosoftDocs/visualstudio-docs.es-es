---
title: 'Inspeccionar variables: ventanas automático y variables locales | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904114"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Inspeccionar las variables en las ventanas automático y variables locales

Las ventanas **automático** y **variables locales** muestran los valores de las variables durante la depuración. Las ventanas solo están disponibles durante una sesión de depuración. La ventana **automático** muestra las variables usadas en torno al punto de interrupción actual. La ventana **variables locales** muestra las variables definidas en el ámbito local, que suele ser la función o el método actual. Si es la primera vez que intenta depurar código, puede que desee leer la [depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de pasar a este artículo.

 La ventana **automático** está disponible para C#, Visual Basic, C++y el código de Python, pero no para JavaScript o F#.

Para abrir la **ventana automático** , durante la depuración, seleccione **depurar** > **Windows** > **automático**o presione **Ctrl**+**Alt**+**V** > **A**.

Para abrir la ventana **variables locales** , durante la depuración, seleccione **depurar** > **Windows** > **variables locales**o presione **Alt**+**4**.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. Para obtener Visual Studio para Mac, vea [visualizaciones de datos en Visual Studio para Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Usar las ventanas automático y variables locales

Las matrices y los objetos se muestran en las ventanas **automático** y **variables locales** como controles de árbol. Seleccione la flecha situada a la izquierda de un nombre de variable para expandir la vista y mostrar los campos y las propiedades. A continuación se muestra un ejemplo de un objeto <xref:System.IO.FileStream?displayProperty=fullName> en la ventana **variables locales** :

![Variables locales-FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")

Un valor rojo en la ventana **variables locales** o **automático** significa que el valor ha cambiado desde la última evaluación. El cambio puede ser de una sesión de depuración anterior o porque ha cambiado el valor en la ventana.

El formato numérico predeterminado en las ventanas del depurador es decimal. Para cambiarlo a hexadecimal, haga clic con el botón derecho en la ventana **variables locales** o **automático** y seleccione **presentación hexadecimal**. Este cambio afecta a todas las ventanas del depurador.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Editar valores de variables en la ventana automático o variables locales

Para editar los valores de la mayoría de las variables en las ventanas **automático** o **variables locales** , haga doble clic en el valor y escriba el nuevo valor.

Puede escribir una expresión para un valor; por ejemplo, `a + b`. El depurador acepta la mayoría de las expresiones de lenguaje válidas.

En el código C++ nativo, se debe calificar el contexto de un nombre de variable. Para obtener más información, vea [Operador de contexto en el depurador de Visual Studio (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Asegúrese de que comprende las consecuencias antes de cambiar los valores y las expresiones. Algunos problemas posibles son:
>
>- La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otra forma al estado del programa. Por ejemplo, la evaluación de `var1 = ++var2` cambia el valor de `var1` y `var2`. Se dice que estas expresiones tienen [efectos secundarios](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden producir resultados inesperados si no se tienen en cuenta.
>
>- La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una edición aparentemente inofensiva puede dar lugar a cambios en algunos de los bits de la variable de punto flotante.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Buscar en la ventana automático o variables locales

Puede buscar palabras clave en las columnas nombre, valor y tipo de la ventana **automático** o **variables locales** mediante la barra de búsqueda situada encima de cada ventana. Presione entrar o seleccione una de las flechas para ejecutar una búsqueda. Para cancelar una búsqueda en curso, seleccione el icono "x" en la barra de búsqueda.

Use las flechas izquierda y derecha (MAYÚS + F3 y F3, respectivamente) para desplazarse por las coincidencias encontradas.

![Buscar en la ventana variables locales](../debugger/media/ee-search-locals.png "Buscar en la ventana variables locales")

Para que la búsqueda sea más o menos exhaustiva, use la lista desplegable **Buscar en profundidad** en la parte superior de la ventana **automático** o **variables locales** para seleccionar cuántos niveles de profundidad desea buscar en objetos anidados. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Anclar propiedades en la ventana automático o variables locales

> [!NOTE]
> Esta característica es compatible con .NET Core 3,0 o superior.

Puede inspeccionar rápidamente los objetos por sus propiedades en las ventanas automático y variables locales con la herramienta **anclar propiedades** .  Para usar esta herramienta, mantenga el mouse sobre una propiedad y seleccione el icono de anclaje que aparece o haga clic con el botón derecho y seleccione la opción **anclar miembro como favorito** en el menú contextual resultante.  Esta propiedad se propaga a la parte superior de la lista de propiedades del objeto y el nombre y el valor de la propiedad se muestra en la columna **valor** .  Para desanclar una propiedad, vuelva a seleccionar el icono de anclaje o seleccione la opción **desanclar miembro como favorito** en el menú contextual.

![Anclar propiedades en la ventana variables locales](../debugger/media/basic-pin.gif "Anclar propiedades en la ventana variables locales")

También puede alternar los nombres de propiedad y filtrar las propiedades no ancladas al ver la lista de propiedades del objeto en las ventanas automático o variables locales.  Puede tener acceso a cada opción seleccionando los botones en la barra de herramientas situada encima de las ventanas automático o variables locales.

![Filtrar propiedades favoritas](../debugger/media/filter-pinned-properties-locals.png "Filtrar propiedades favoritas")
![alternar nombres de propiedad](../debugger/media/toggle-property-names.gif "Alternar nombres de propiedad")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Cambiar el contexto de la ventana automático o variables locales

Puede usar la barra de herramientas **Ubicación de depuración** para seleccionar la función, el subproceso o el proceso que desee, que cambia el contexto de las ventanas **automático** y **variables locales** .

Para habilitar la barra de herramientas **Ubicación de depuración** , haga clic en una parte vacía del área de la barra de herramientas y seleccione **Ubicación de depuración** en la lista desplegable o seleccione **ver** > **barras de herramientas** > **Ubicación de depuración**.

Establezca un punto de interrupción e inicie la depuración. Cuando se alcanza el punto de interrupción, la ejecución se detiene y se puede ver la ubicación en la barra de herramientas **Ubicación de depuración** .

![Barra de herramientas ubicación de depuración](../debugger/media/debuglocationtoolbar.png "Barra de herramientas Ubicación de depuración")

## <a name="bkmk_whatvariables"></a>Variables en la ventana automático (C#, C++, Visual Basic, Python)

Los distintos lenguajes de código muestran variables diferentes en la ventana **automático** .

- En C# y Visual Basic, la ventana **Automático** muestra cualquier variable que se usa en la línea actual o anterior. Por ejemplo, en C# o Visual Basic código, declare las cuatro variables siguientes:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Establezca un punto de interrupción en la línea `c = 3;`e inicie el depurador. Cuando se detiene la ejecución, se muestra la ventana **automático** :

   ![Auto-CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")

   El valor de `c` es 0, porque la línea `c = 3` aún no se ha ejecutado.

- En C++, la ventana **automático** muestra las variables que se usan en al menos tres líneas antes de la línea actual en la que se pausa la ejecución. Por ejemplo, en C++ el código, declare seis variables:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Establezca un punto de interrupción en la línea `e = 5;` y ejecute el depurador. Cuando se detenga la ejecución, se mostrará la ventana **automático** :

    ![AutomáticoC++](../debugger/media/autos-cplus.png "AutomáticoC++")

    La variable `e` no está inicializada porque el `e = 5` de línea aún no se ha ejecutado.

## <a name="bkmk_returnValue"></a> View return values of method calls
 En .NET y C++ en el código, puede examinar los valores devueltos en la ventana **automático** al recorrer o salir de una llamada al método. La visualización de los valores devueltos de la llamada al método puede resultar útil cuando no se almacenan en variables locales. Un método se puede usar como parámetro o como valor devuelto de otro método.

 Por ejemplo, el código C# siguiente agrega los valores devueltos de dos funciones:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

Para ver los valores devueltos de las llamadas al método `sumVars()` y `subtractVars()` en la ventana automático:

1. Establezca un punto de interrupción en la línea `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Inicie la depuración y, cuando la ejecución se pausa en el punto de interrupción, seleccione **paso a paso por procedimientos** o presione **F10**. Debería ver los valores devueltos siguientes en la ventana **automático** :

  ![Valor devuelto automáticoC#](../debugger/media/autosreturnvaluecsharp2.png "Valor devuelto automáticoC#")

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ventanas del depurador](../debugger/debugger-windows.md)
