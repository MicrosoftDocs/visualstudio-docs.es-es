---
title: 'Inspección de variables: ventanas Automático y Variables locales | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: how-to
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
ms.openlocfilehash: 3ae67fadf5d9710f2088f47617b74eeeb8212826
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350750"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Inspección de variables en las ventanas Automático y Variables locales

Las ventanas **Automático** y **Variables locales** muestran valores de variables durante la depuración. Las ventanas solo están disponibles durante una sesión de depuración. La ventana **Automático** muestra las variables usadas en torno al punto de interrupción actual. La ventana **Variables locales** muestra las variables definidas en el ámbito local, que suele ser la función o el método actuales. Si esta es la primera vez que intenta depurar código, le recomendamos que lea [Cómo depurar para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md) y [Herramientas y técnicas de depuración para ayudarle a escribir código de mayor calidad](../debugger/write-better-code-with-visual-studio.md) antes de continuar con este artículo.

 La ventana **Automático** está disponible para código de C#, Visual Basic, C++ y Python, pero no de JavaScript o F#.

Para abrir la ventana **Automático**, seleccione **Depurar** > **Ventanas** > **Automático**, o bien presione **Ctrl**+**Alt**+**V** > **A** durante la depuración.

Para abrir la ventana **Variables locales**, seleccione **Depurar** > **Ventanas** > **Variables locales**, o bien presione **Alt**+**4** durante la depuración.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Visualizaciones de datos](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Uso de las ventanas Automático y Variables locales

Las matrices y los objetos se muestran en las ventanas **Automático** y **Variables locales** como controles de árbol. Seleccione la flecha situada a la izquierda del nombre de una variable para expandir la vista y mostrar los campos y las propiedades. En el ejemplo siguiente se muestra un objeto <xref:System.IO.FileStream?displayProperty=fullName> en la ventana **Variables locales**:

![FileStream en Variables locales](../debugger/media/locals-filestream.png "FileStream en Variables locales")

Un valor en rojo en la ventana **Variables locales** o **Automático** indica que el valor ha cambiado desde la última evaluación. La causa del cambio podría ser una sesión de depuración anterior o la modificación del valor en la ventana.

El formato numérico predeterminado de las ventanas del depurador es decimal. Para cambiarlo a hexadecimal, haga clic con el botón derecho en la ventana **Variables locales** o **Automático** y seleccione **Presentación hexadecimal**. El cambio afecta a todas las ventanas del depurador.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Edición de valores de variable en las ventanas Automático y Variables locales

Para editar los valores de la mayoría de las variables en las ventanas **Automático** o **Variables locales**, haga doble clic en el valor y escriba el nuevo valor.

Puede escribir una expresión para un valor; por ejemplo, `a + b`. El depurador acepta la mayoría de las expresiones de lenguaje válidas.

En el código C++ nativo, se debe calificar el contexto de un nombre de variable. Para obtener más información, vea [Operador de contexto en el depurador de Visual Studio (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Asegúrese de que comprende las consecuencias antes de cambiar valores y expresiones. Estas son algunos problemas posibles:
>
>- La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otra forma al estado del programa. Por ejemplo, al evaluar `var1 = ++var2` se cambia el valor de `var1` y `var2`. Se dice que estas expresiones tienen [efectos secundarios](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden producir resultados inesperados si no se tienen en cuenta.
>
>- La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inofensiva puede causar cambios en alguno de los bits de la variable de punto flotante.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Búsqueda en las ventanas Automático o Variables locales

Puede buscar palabras clave en las columnas Nombre, Valor y Tipo de la ventana **Automático** o **Variables locales** mediante la barra de búsqueda situada encima de cada ventana. Presione Entrar o seleccione una de las flechas para ejecutar una búsqueda. Para cancelar una búsqueda en curso, seleccione el icono "x" en la barra de búsqueda.

Use las flechas izquierda y derecha (Mayús+F3 y F3, respectivamente) para desplazarse por las coincidencias encontradas.

![Búsqueda en la ventana Variables locales](../debugger/media/ee-search-locals.png "Búsqueda en la ventana Variables locales")

Para que la búsqueda sea más o menos exhaustiva, use la lista desplegable **Profundizar la búsqueda** en la parte superior de la ventana **Automático** o **Variables locales** para seleccionar en cuántos niveles de profundidad quiere buscar objetos anidados. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Anclaje de propiedades en la ventana Automático o Variables locales

> [!NOTE]
> Esta característica es compatible con .NET Core 3.0 o versiones posteriores.

Puede inspeccionar rápidamente objetos por sus propiedades en las ventanas Automático y Variables locales con la **herramienta para anclar propiedades**.  Para usar esta herramienta, mantenga el puntero sobre una propiedad y seleccione el icono Anclar que aparece o haga clic con el botón derecho y seleccione la opción **Anclar miembro como favorito** en el menú contextual resultante.  Esta propiedad se propaga a la parte superior de la lista de propiedades del objeto, y el nombre y el valor de la propiedad se muestran en la columna **Valor**.  Para desanclar una propiedad, vuelva a seleccionar el icono para anclar o seleccione la opción **Desanclar miembro como favorito** en el menú contextual.

![Anclaje de propiedades en la ventana Variables locales](../debugger/media/basic-pin.gif "Anclaje de propiedades en la ventana Variables locales")

También puede alternar los nombres de propiedades y filtrar las no ancladas al consultar la lista de propiedades del objeto en las ventanas Automático o Variables locales.  Puede acceder a ambas opciones seleccionando los botones en la barra de herramientas situada encima de las ventanas Automático o Variables locales.

![Filter favorite properties](../debugger/media/filter-pinned-properties-locals.png "Filtrado de propiedades favoritas")
![Toggle property names](../debugger/media/toggle-property-names.gif "Alternancia de nombres de propiedad") (Filtrar propiedades favoritas > Alternar nombres de propiedad)

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Cambio del contexto de la ventana Automático o Variables locales

Puede usar la barra de herramientas **Ubicación de depuración** para seleccionar la función, el subproceso o el proceso que quiera, lo que cambia el contexto de las ventanas **Automático** y **Variables locales**.

Para habilitar la barra de herramientas **Ubicación de depuración**, haga clic en una parte vacía del área de la barra de herramientas y seleccione **Ubicación de depuración** en la lista desplegable, o bien seleccione **Ver** > **Barras de herramientas** > **Ubicación de depuración**.

Establezca un punto de interrupción e inicie la depuración. Cuando se alcanza el punto de interrupción, la ejecución se pausa y puede verse la ubicación en la barra de herramientas **Ubicación de depuración**.

![Barra de herramientas Ubicación de depuración](../debugger/media/debuglocationtoolbar.png "Barra de herramientas Ubicación de depuración")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Variables en la ventana Automático (C#, C++, Visual Basic, Python)

Los diferentes lenguajes de código muestran distintas variables en la ventana**Automático**.

- En C# y Visual Basic, la ventana **Automático** muestra cualquier variable que se usa en la línea actual o anterior. Por ejemplo, en código de C# o Visual Basic, declare las cuatro variables siguientes:

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

   Establezca un punto de interrupción en la línea `c = 3;` e inicie el depurador. Cuando la ejecución se pause, se mostrará la ventana **Automático**:

   ![CSharp en Automático](../debugger/media/autos-csharp.png "CSharp en Automático")

   El valor de `c` es 0, porque la línea `c = 3` aún no se ha ejecutado.

- En C++, la ventana **Automático** muestra las variables que se usan en al menos tres líneas anteriores a la línea actual, en la que la ejecución se pausa. Por ejemplo, en código C++, declare seis variables:

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

    Establezca un punto de interrupción en la línea `e = 5;` y ejecute el depurador. Cuando la ejecución se detenga, se mostrará la ventana **Automático**:

    ![C++ en Automático](../debugger/media/autos-cplus.png "C++ en Automático")

    La variable `e` no se ha inicializado porque la línea `e = 5` aún no se ha ejecutado.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 En el código .NET y C++ se pueden examinar los valores en la ventana **Automático** cuando una llamada al método se ejecuta paso a paso por procedimientos o paso a paso para salir. La visualización de los valores devueltos de la llamada de método puede resultar útil cuando no se almacenan en variables locales. Un método se puede usar como parámetro o como valor devuelto de otro método.

 Por ejemplo, el siguiente código C# agrega los valores devueltos de dos funciones:

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

Para ver los valores devueltos de las llamadas de método `sumVars()` y `subtractVars()` en la ventana Automático:

1. Establezca un punto de interrupción en la línea `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Inicie la depuración y, cuando la ejecución se pause en el punto de interrupción, seleccione **Paso a paso por procedimientos** o presione **F10**. Deberían mostrarse los siguientes valores devueltos en la ventana **Automático**:

  ![Valor devuelto de C# en Automático](../debugger/media/autosreturnvaluecsharp2.png "Valor devuelto de C# en Automático")

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ventanas del depurador](../debugger/debugger-windows.md)
