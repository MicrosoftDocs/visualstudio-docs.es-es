---
title: Establecer un reloj en las variables | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904057"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Inspección de variables con ventanas inspección e inspección rápida

Mientras realiza la depuración, puede usar **inspección** de ventanas e **Inspección rápida** para ver variables y expresiones. Las ventanas solo están disponibles durante una sesión de depuración.

Las ventanas de **inspección** pueden mostrar varias variables a la vez durante la depuración. El cuadro de diálogo **Inspección rápida** muestra una sola variable cada vez y debe cerrarse para que la depuración pueda continuar.

Si es la primera vez que intenta depurar código, puede que desee leer la [depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de pasar a este artículo.

## <a name="observe-variables-with-a-watch-window"></a>Observar las variables con un ventana Inspección

Puede abrir más de una ventana **inspección** y observar más de una variable en una ventana **inspección** .

Por ejemplo, para establecer un reloj sobre los valores de `a`, `b`y `c` en el código siguiente:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Establezca un punto de interrupción en la línea de `c = a + b;`; para ello, haga clic en el margen izquierdo, seleccione **Depurar** > **alternar punto de interrupción**o presione **F9**.

1. Inicie la depuración seleccionando la flecha de **Inicio** verde o **depurar** > **iniciar depuración**o presione **F5**. La ejecución se detiene en el punto de interrupción.

1. Abra una ventana **inspección** seleccionando **depurar** > **Windows** > **watch** > **inspección 1**o **presionando Ctrl**+**Alt**+**W** > **1**.

   Puede abrir ventanas de **inspección** adicionales seleccionando Windows **2**, **3**o **4**.

1. En la ventana **inspección** , seleccione una fila vacía y escriba la variable `a`. Haga lo mismo para `b` y `c`.

   ![Variables de inspección](../debugger/media/watchvariables.png "WatchVariables")

1. Continúe con la depuración seleccionando **Depurar** > **paso a paso** por instrucciones o presionando **F11** según sea necesario para avanzar. Los valores de las variables de la ventana **inspección** cambian a medida que se recorre en iteración el bucle `for`.

>[!NOTE]
>Solo C++ para,
>- Es posible que deba calificar el contexto de un nombre de variable o una expresión que use un nombre de variable. El contexto es la función, el archivo de código fuente o el módulo donde se encuentra una variable. Si tiene que calificar el contexto, use la sintaxis del [operadorC++de contexto ()](../debugger/context-operator-cpp.md) en el **nombre** de la ventana **inspección** .
>
>- Puede Agregar nombres de registro y nombres de variable mediante **$\<nombre de&nbsp;de registro >** o **@\<registrar&nbsp;nombre** > en el **nombre** de la ventana **inspección** . Para obtener más información, consulta [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usar expresiones en un ventana Inspección

Puede observar cualquier expresión válida reconocida por el depurador en una ventana **inspección** .

Por ejemplo, para el código de la sección anterior, puede obtener el promedio de los tres valores escribiendo `(a + b + c) / 3` en la ventana **inspección** :

![Expresión de inspección](../debugger/media/watchexpression.png "Expresión de inspección")

Las reglas para evaluar las expresiones en la ventana **inspección** suelen ser las mismas que las reglas para evaluar expresiones en el lenguaje de código. Si una expresión tiene un error de sintaxis, se espera el mismo error del compilador que en el editor de código. Por ejemplo, un error tipográfico en la expresión anterior produce este error en la ventana **inspección** :

![Error de la expresión de inspección](../debugger/media/watchexpressionerror.png "Error de la expresión de inspección")

Puede aparecer un círculo con dos líneas onduladas en la ventana **inspección** . Este icono significa que el depurador no evalúa la expresión debido a una posible dependencia entre subprocesos. La evaluación del código requiere que otros subprocesos de la aplicación se ejecuten de forma temporal, pero como está en modo de interrupción, se suelen detener todos los subprocesos de la aplicación. Permitir que otros subprocesos se ejecuten temporalmente puede tener efectos inesperados en el estado de la aplicación y el depurador puede omitir eventos como puntos de interrupción y excepciones en esos subprocesos.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Busque en el ventana Inspección

Puede buscar palabras clave en las columnas nombre, valor y tipo de la ventana **inspección** mediante la barra de búsqueda situada encima de cada ventana. Presione entrar o seleccione una de las flechas para ejecutar una búsqueda. Para cancelar una búsqueda en curso, seleccione el icono "x" en la barra de búsqueda.

Use las flechas izquierda y derecha (MAYÚS + F3 y F3, respectivamente) para desplazarse por las coincidencias encontradas.

![Buscar en la ventana Inspección](../debugger/media/ee-search-watch.png "Buscar en la ventana Inspección")

Para que la búsqueda sea más o menos exhaustiva, use la lista desplegable **Buscar en profundidad** en la parte superior de la ventana **inspección** para seleccionar cuántos niveles de profundidad desea buscar en objetos anidados. 

## <a name="pin-properties-in-the-watch-window"></a>Anclar propiedades en el ventana Inspección

>[!NOTE]
> Esta característica se admite en .NET Core 3,0 o superior.

Puede inspeccionar rápidamente los objetos por sus propiedades en el ventana Inspección con la herramienta **anclar propiedades** .  Para usar esta herramienta, mantenga el mouse sobre una propiedad y seleccione el icono de anclaje que aparece o haga clic con el botón derecho y seleccione la opción **anclar miembro como favorito** en el menú contextual resultante.  Esta propiedad se propaga a la parte superior de la lista de propiedades del objeto y el nombre y el valor de la propiedad se muestra en la columna **valor** .  Para desanclar una propiedad, vuelva a seleccionar el icono de anclaje o seleccione la opción **desanclar miembro como favorito** en el menú contextual.

![Anclar propiedades en el ventana Inspección](../debugger/media/basic-pin-watch.gif "Anclar propiedades en el ventana Inspección")

También puede alternar los nombres de propiedad y filtrar las propiedades no ancladas al ver la lista de propiedades del objeto en el ventana Inspección.  Puede tener acceso a ambas opciones si selecciona los botones en la barra de herramientas situada encima de la ventana Inspección.

::: moniker-end

### <a name="bkmk_refreshWatch"></a>Actualizar valores de inspección

Es posible que aparezca un icono de actualización (flecha circular) en la ventana **inspección** cuando se evalúa una expresión. El icono de actualización indica un error o un valor que no está actualizado.

Para actualizar el valor, seleccione el icono de actualización o presione la barra espaciadora. El depurador intenta evaluar de nuevo la expresión. Sin embargo, es posible que no desee o pueda volver a evaluar la expresión, en función de la razón por la que no se haya evaluado el valor.

Mantenga el mouse sobre el icono de actualización o vea la columna **valor** por la razón por la que no se evaluó la expresión. Entre los motivos se incluyen:

- Se produjo un error mientras se evaluaba la expresión, como en el ejemplo anterior. Es posible que se agote el tiempo de espera o que una variable esté fuera del ámbito.

- La expresión tiene una llamada de función que podría desencadenar un efecto secundario en la aplicación. Consulte [efectos secundarios](#bkmk_sideEffects)de las expresiones.

- La evaluación automática de las propiedades y las llamadas de función implícitas está deshabilitada.

Si el icono de actualización aparece porque la evaluación automática de las propiedades y las llamadas de función implícitas está deshabilitada, puede habilitarla seleccionando **Habilitar evaluación de propiedades y otras llamadas a función implícitas** en **herramientas** > **opciones** > **depuración** > **General**.

Para mostrar el uso del icono de actualización:

1. En **herramientas** > **Opciones** > **depuración** > **General**, desactive la casilla **Habilitar evaluación de propiedades y otras llamadas a función implícitas** .

1. Escriba el código siguiente y, en la ventana **inspección** , establezca un reloj en la propiedad `list.Count`.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Inicie la depuración. La ventana **inspección** muestra algo parecido al siguiente mensaje:

   ![Actualizar inspección](../debugger/media/refreshwatch.png "Actualizar inspección")

1. Para actualizar el valor, seleccione el icono de actualización o presione la barra espaciadora. El depurador vuelve a evaluar la expresión.

### <a name="bkmk_sideEffects"></a>Efectos secundarios de las expresiones

La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de algún modo al estado de la aplicación. Por ejemplo, la evaluación de la siguiente expresión cambia el valor de `var1`:

```csharp
var1 = var2
```

Este código puede producir un [efecto secundario](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden dificultar la depuración cambiando la forma en que funciona la aplicación.

Una expresión con efectos secundarios se evalúa solo una vez, la primera vez que se escribe. Después, la expresión aparece atenuada en la ventana **inspección** y las evaluaciones adicionales están deshabilitadas. La información sobre herramientas o la columna **valor** explica que la expresión produce un efecto secundario. Puede forzar la reevaluación seleccionando el icono de actualización que aparece junto al valor.

Una manera de evitar la designación de efectos secundarios es desactivar la evaluación automática de funciones. En **herramientas** > **Opciones** > **depuración** > **General**, anule la selección de **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

Solo C# para, cuando se desactiva la evaluación de propiedades o las llamadas a funciones IMPLÍCITAS, puede forzar la evaluación agregando el modificador de formato **AC** a un **nombre** de variable en la ventana **inspección** . Vea [Format Specifiers in C#](../debugger/format-specifiers-in-csharp.md) (Especificadores de formato en C#).

## <a name="bkmk_objectIds"></a>Usar identificadores de objeto en elC# ventana Inspección (y Visual Basic)

A veces, desea observar el comportamiento de un objeto específico. Por ejemplo, puede que desee realizar el seguimiento de un objeto al que hace referencia una variable local después de que dicha variable haya salido del ámbito. En C# y Visual Basic, puede crear identificadores de objetos para instancias específicas de tipos y usarlos en la ventana **Inspección** y en condiciones de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles que no impiden que el objeto se recopile como elemento no utilizado. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

En el código siguiente, el método `MakePerson()` crea un `Person` mediante una variable local:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Para averiguar el nombre del `Person` en el método `DoSomething()`, puede Agregar una referencia al identificador de objeto `Person` en la ventana **inspección** .

1. Establezca un punto de interrupción en el código una vez creado el objeto de `Person`.

1. Inicie la depuración.

1. Cuando la ejecución se detiene en el punto de interrupción, abra la ventana **variables locales** eligiendo **depurar** > **Windows** > **variables locales**.

1. En la ventana **variables locales** , haga clic con el botón secundario en la variable `Person` y seleccione **crear ID**. de objeto.

   Debería ver un signo de dólar ( **$** ) más un número en la ventana **variables locales** , que es el identificador de objeto.

1. Agregue el identificador de objeto a la ventana **inspección** haciendo clic con el botón secundario en el identificador de objeto y seleccionando **Agregar inspección**.

1. Establezca otro punto de interrupción en el método `DoSomething()`.

1. Continúe la depuración. Cuando la ejecución se pausa en el método `DoSomething()`, la ventana **inspección** muestra el objeto `Person`.

   > [!NOTE]
   > Si desea ver las propiedades del objeto, como `Person.Name`, debe habilitar la evaluación de propiedades seleccionando **herramientas** > **Opciones** > **depuración** > **General** > **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

## <a name="dynamic-view-and-the-watch-window"></a>Vista dinámica y el ventana Inspección

Algunos lenguajes de scripting (por ejemplo, JavaScript o Python) usan tipos dinámicos o de [pato](https://en.wikipedia.org/wiki/Duck_typing) y la versión 4,0 de .net y versiones posteriores admiten objetos que son difíciles de observar en las ventanas de depuración normales.

La ventana **inspección** muestra estos objetos como objetos dinámicos, que se crean a partir de tipos que implementan la interfaz <xref:System.Dynamic.IDynamicMetaObjectProvider>. Los nodos de objeto dinámico muestran los miembros dinámicos de los objetos dinámicos, pero no permiten la edición de los valores de miembro.

Para actualizar los valores de **vista dinámica** , seleccione el [icono de actualización](#bkmk_refreshWatch) situado junto al nodo de objeto dinámico.

Para mostrar solo la **vista dinámica** de un objeto, agregue un especificador de formato **dinámico** después del nombre del objeto dinámico en la ventana **inspección** :

- Para C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- El C# depurador no vuelve a evaluar automáticamente los valores de la **vista dinámica** al pasar a la siguiente línea de código.
>- El depurador de Visual Basic actualiza automáticamente las expresiones agregadas a través de la **vista dinámica**.
>- La evaluación de los miembros de una **vista dinámica** puede tener [efectos secundarios](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Para insertar una nueva variable de inspección que convierta un objeto en un objeto dinámico:**

1. Haga clic con el botón secundario en cualquier elemento secundario de una **vista dinámica**.
1. Elija **Agregar inspección**. El `object.name` se `((dynamic) object).name` y aparece en una nueva ventana de **inspección** .

El depurador también agrega un nodo secundario de **vista dinámica** del objeto a la ventana **automático** . Para abrir la ventana **automático** , durante la depuración, seleccione **depurar** > **Windows** > **automático**.

La **vista dinámica** también mejora la depuración de objetos com. Cuando el depurador llega a un objeto COM ajustado en **System. __ComObject**, agrega un nodo **vista dinámica** para el objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observar una sola variable o expresión con Inspección rápida

Puede usar **Inspección rápida** para observar una única variable.

Por ejemplo, para el código siguiente:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Para observar la variable `a`,

1. Establezca un punto de interrupción en la línea `a = a + b;` .

1. Inicie la depuración. La ejecución se detiene en el punto de interrupción.

1. Seleccione la variable `a` en el código.

1. Seleccione **Depurar** > **Inspección rápida**, presione **MAYÚS**+**F9**o haga clic con el botón derecho y seleccione **Inspección rápida**.

   Aparece el cuadro de diálogo **Inspección rápida** . La variable `a` está en el cuadro **expresión** con un **valor** de **1**.

   ![Inspección rápida (variable)](../debugger/media/quickwatchvariable.png "Inspección rápida (variable)")

1. Para evaluar una expresión mediante la variable, escriba una expresión como `a + b` en el cuadro **expresión** y seleccione volver a **evaluar**.

   ![Expresión de inspección rápida](../debugger/media/quickwatchexpression.png "Expresión de inspección rápida")

1. Para agregar la variable o expresión de **Inspección rápida** a la ventana **inspección** , seleccione **Agregar inspección**.

1. Seleccione **cerrar** para cerrar la ventana **Inspección rápida** . (**Inspección rápida** es un cuadro de diálogo modal, por lo que no puede continuar con la depuración mientras esté abierto).

1. Continúe la depuración. Puede observar la variable en la ventana **inspección** .

## <a name="see-also"></a>Vea también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ventanas del depurador](../debugger/debugger-windows.md)
