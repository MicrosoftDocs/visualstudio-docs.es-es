---
title: Fije un reloj en las variables de la unidad de la unidad de la unidad de la unidad de la unidad de Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301018"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Ver variables con ventanas de reloj y quickwatch

Mientras está depurando, puede usar **Ventanas** de inspección y **Inspección rápida** para ver variables y expresiones. Las ventanas solo están disponibles durante una sesión de depuración.

**Las** ventanas de inspección pueden mostrar varias variables a la vez durante la depuración. El cuadro de diálogo **Inspección rápida** muestra una única variable a la vez y debe cerrarse antes de que la depuración pueda continuar.

Si es la primera vez que intenta depurar código, es posible que desee leer [Depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [técnicas y herramientas](../debugger/write-better-code-with-visual-studio.md) de depuración antes de pasar por este artículo.

## <a name="observe-variables-with-a-watch-window"></a>Observar variables con una ventana Reloj

Puede abrir más de una ventana **De inspección** y observar más de una variable en una ventana **Inspección.**

Por ejemplo, para establecer un `a`reloj `b`en `c` los valores de , , y en el código siguiente:

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

1. Establezca un punto `c = a + b;` de interrupción en la línea haciendo clic en el margen izquierdo, seleccionando **Depurar** > alternar punto de**interrupción**o presionando **F9**.

1. Inicie la depuración seleccionando la flecha verde **Inicio** o **Depurar depuración** > **de inicio**o presione **F5**. La ejecución se detiene en el punto de interrupción.

1. Abra una ventana **Ver** seleccionando **Depurar** > **Windows** > **Watch** > **Watch 1**o pulsando **Ctrl**+**Alt**+**W** > **1**.

   Puede abrir ventanas de **inspección** adicionales seleccionando ventanas **2**, **3**o **4**.

1. En la ventana **Inspección,** seleccione una `a`fila vacía y escriba la variable . Haga lo `b` mismo `c`para y .

   ![Ver variables](../debugger/media/watchvariables.png "WatchVariables")

1. Continúe la depuración seleccionando **Depurar** > **paso** a o presionando **F11** según sea necesario para avanzar. Los valores de variable de la ventana **Inspección** cambian a medida que recorre en iteración el `for` bucle.

>[!NOTE]
>Sólo para C++,
>- Es posible que deba calificar el contexto de un nombre de variable o una expresión que utilice un nombre de variable. El contexto es la función, el archivo de origen o el módulo donde se encuentra una variable. Si tiene que calificar el contexto, utilice la sintaxis del operador de [contexto (C++)](../debugger/context-operator-cpp.md) en el **nombre** en la ventana **Inspección.**
>
>- Puede agregar nombres de registro y nombres de variables **Name** mediante ** $ \<&nbsp;** el nombre de registro>o ** @ \<&nbsp;** el nombre de registro>al nombre en la ventana **Inspección.** Para obtener más información, consulta [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usar expresiones en una ventana Inspección

Puede observar cualquier expresión válida reconocida por el depurador en una ventana **Inspección.**

Por ejemplo, para el código de la sección anterior, puede obtener `(a + b + c) / 3` el promedio de los tres valores introduciendo en la ventana **Inspección:**

![Ver expresión](../debugger/media/watchexpression.png "Ver expresión")

Las reglas para evaluar expresiones en la ventana **Inspección** son generalmente las mismas que las reglas para evaluar expresiones en el lenguaje de código. Si una expresión tiene un error de sintaxis, espere el mismo error del compilador que en el editor de código. Por ejemplo, un error tipográfico en la expresión anterior produce este error en la ventana **Inspección:**

![Error de expresión de inspección](../debugger/media/watchexpressionerror.png "Error de expresión de inspección")

Un círculo con dos líneas onduladas puede aparecer en la ventana **Inspección.** Este icono significa que el depurador no evalúa la expresión debido a una posible dependencia entre subprocesos. La evaluación del código requiere que otros subprocesos de la aplicación se ejecuten temporalmente, pero como está en modo de interrupción, todos los subprocesos de la aplicación normalmente se detienen. Permitir que otros subprocesos se ejecuten temporalmente puede tener efectos inesperados en el estado de la aplicación y el depurador puede omitir eventos como puntos de interrupción y excepciones en esos subprocesos.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Buscar en la ventana Inspección

Puede buscar palabras clave en las columnas Nombre, Valor y Tipo de la ventana **Inspección** mediante la barra de búsqueda situada encima de cada ventana. Pulse ENTER o seleccione una de las flechas para ejecutar una búsqueda. Para cancelar una búsqueda en curso, seleccione el icono "x" en la barra de búsqueda.

Utilice las flechas izquierda y derecha (Mayús+F3 y F3, respectivamente) para navegar entre las coincidencias encontradas.

![Buscar en la ventana de inspección](../debugger/media/ee-search-watch.png "Buscar en la ventana de inspección")

Para que la búsqueda sea más o menos exhaustiva, utilice el menú desplegable **Buscar más profundo** en la parte superior de la ventana **Inspección** para seleccionar cuántos niveles de profundidad desea buscar en objetos anidados. 

## <a name="pin-properties-in-the-watch-window"></a>Propiedades de ancleen en la ventana Inspección

>[!NOTE]
> Esta característica se admite en .NET Core 3.0 o superior.

Puede inspeccionar rápidamente los objetos por sus propiedades en la ventana Inspección con la herramienta **Propiedades anclables.**  Para utilizar esta herramienta, coloque el cursor sobre una propiedad y seleccione el icono de pasador que aparece o haga clic con el botón derecho y seleccione la opción **Anclar miembro como favorito** en el menú contextual resultante.  Esto propaga esa propiedad en la parte superior de la lista de propiedades del objeto y el nombre y el valor de la propiedad se muestran en la columna **Valor.**  Para desanclar una propiedad, vuelva a seleccionar el icono de pasador o seleccione la opción **Desanclar miembro como favorito** en el menú contextual.

![Propiedades de ancleen en la ventana Inspección](../debugger/media/basic-pin-watch.gif "Propiedades de ancleen en la ventana Inspección")

También puede alternar los nombres de propiedad y filtrar las propiedades no ancladas al ver la lista de propiedades del objeto en la ventana Inspección.  Puede acceder a ambas opciones seleccionando los botones de la barra de herramientas situada encima de la ventana del reloj.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Actualizar los valores del reloj

Es posible que aparezca un icono de actualización (flecha circular) en la ventana **Inspección** cuando se evalúe una expresión. El icono de actualización indica un error o un valor que está desactualizado.

Para actualizar el valor, seleccione el icono de actualización o pulse la barra espaciadora. El depurador intenta evaluar de nuevo la expresión. Sin embargo, es posible que no desee o pueda volver a evaluar la expresión, dependiendo de por qué no se evaluó el valor.

Pase el cursor sobre el icono de actualización o vea la columna **Valor** por el motivo por el que no se evaluó la expresión. Los motivos incluyen los siguientes:

- Se ha producido un error cuando se estaba evaluando la expresión, como en el ejemplo anterior. Puede producirse un tiempo de espera o una variable fuera del ámbito.

- La expresión tiene una llamada de función que podría desencadenar un efecto secundario en la aplicación. Consulte [Efectos secundarios](#bkmk_sideEffects)de expresión .

- La evaluación automática de propiedades y llamadas de función implícitas está deshabilitada.

Si el icono de actualización aparece porque la evaluación automática de propiedades y llamadas de función implícitas está deshabilitada, puede habilitarlo seleccionando Habilitar evaluación de propiedades y otras llamadas de **función implícitas** en **Opciones** > **Options** > de herramientas**Depuración** > **general**.

Para demostrar el uso del icono de actualización:

1. En **Tools** > **Opciones** > de herramientas**Depuración** > **general**, desactive la casilla Habilitar evaluación de propiedades y otras **llamadas de función implícitas.**

1. Escriba el código siguiente y, en la ventana `list.Count` **Inspección,** establezca un reloj en la propiedad.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Inicie la depuración. La ventana **Inspección** muestra algo como el siguiente mensaje:

   ![Actualizar reloj](../debugger/media/refreshwatch.png "Actualizar reloj")

1. Para actualizar el valor, seleccione el icono de actualización o pulse la barra espaciadora. El depurador vuelve a evaluar la expresión.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Efectos secundarios de la expresión

La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otro modo al estado de la aplicación. Por ejemplo, la evaluación de la siguiente expresión cambia el valor de `var1`:

```csharp
var1 = var2
```

Este código puede causar un [efecto secundario](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden dificultar la depuración cambiando la forma en que funciona la aplicación.

Una expresión con efectos secundarios se evalúa una sola vez, cuando se introduce por primera vez. Después de eso, la expresión aparece atenuada en la ventana **Inspección** y se deshabilitan otras evaluaciones. La información sobre herramientas o la columna **Value** explica que la expresión provoca un efecto secundario. Puede forzar la reevaluación seleccionando el icono de actualización que aparece junto al valor.

Una manera de prevenir la designación de efectos secundarios es desactivar la evaluación automática de la función. En **Tools** > **Opciones** > de herramientas**Depuración** > **general**, anule la selección de Habilitar evaluación de propiedades y otras **llamadas de función implícitas**.

Solo para C, cuando se desactiva la evaluación de propiedades o llamadas de función implícitas, puede forzar la evaluación agregando el modificador de formato **AC** a una variable **Name** en la ventana **Inspección.** Consulte Formato de [especificadores en C.](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Usar los identificadores de objeto en la ventana Inspección (C- y Visual Basic)

A veces desea observar el comportamiento de un objeto específico. Por ejemplo, es posible que desee realizar un seguimiento de un objeto al que hace referencia una variable local después de que esa variable haya salido del ámbito. En C- y Visual Basic, puede crear identificadores de objeto para instancias específicas de tipos de referencia y usarlos en la ventana **Inspección** y en condiciones de punto de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles que no impiden que el objeto se recopile. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

En el código `MakePerson()` siguiente, `Person` el método crea una variable using a local:

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

Para averiguar el nombre `Person` del `DoSomething()` método, puede agregar una `Person` referencia al identificador de objeto en la ventana **Inspección.**

1. Establezca un punto de interrupción en el código después de crear el `Person` objeto.

1. Inicie la depuración.

1. Cuando la ejecución se detenga en el punto de interrupción, abra la ventana **Locales** seleccionando **Depurar** > **locales de****Windows** > .

1. En la ventana **Locales,** `Person` haga clic con el botón derecho en la variable y seleccione **Crear ID de objeto**.

   Debería ver un signo**$** de dólar ( ) más un número en la ventana **Locales,** que es el IDENTIFICADOR de objeto.

1. Agregue el ID de objeto a la ventana **Inspección** haciendo clic con el botón derecho en el ID de objeto y seleccionando **Agregar inspección**.

1. Establezca otro punto `DoSomething()` de interrupción en el método.

1. Continúe la depuración. Cuando la ejecución `DoSomething()` se detiene en `Person` el método, la ventana **Inspección** muestra el objeto.

   > [!NOTE]
   > Si `Person.Name`desea ver las propiedades del objeto, como , debe habilitar la evaluación de propiedades seleccionando **Tools** > **Opciones** > de herramientas**Depuración** > **general** > Habilitar evaluación de propiedades y otras**llamadas de función implícitas**.

## <a name="dynamic-view-and-the-watch-window"></a>Vista dinámica y la ventana Inspección

Algunos lenguajes de scripting (por ejemplo, JavaScript o Python) usan escritura dinámica o [pato,](https://en.wikipedia.org/wiki/Duck_typing) y .NET versión 4.0 y versiones posteriores admiten objetos que son difíciles de observar en las ventanas de depuración normales.

La ventana **Inspección** muestra estos objetos como objetos <xref:System.Dynamic.IDynamicMetaObjectProvider> dinámicos, que se crean a partir de tipos que implementan la interfaz. Los nodos de objetos dinámicos muestran los miembros dinámicos de los objetos dinámicos, pero no permiten la edición de los valores de miembro.

Para actualizar los valores de **la vista dinámica,** seleccione el icono de [actualización](#bkmk_refreshWatch) situado junto al nodo de objeto dinámico.

Para mostrar solo la **vista dinámica** de un objeto, agregue un especificador de formato **dinámico** después del nombre del objeto dinámico en la ventana **Inspección:**

- Para C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- El depurador de C- no reevalua automáticamente los valores de la **vista dinámica** cuando se pasa a la siguiente línea de código.
>- El depurador de Visual Basic actualiza automáticamente las expresiones agregadas a través de la **vista dinámica**.
>- La evaluación de los miembros de una **vista dinámica** puede tener [efectos secundarios.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))

**Para insertar una nueva variable de inspección que convierte un objeto en un objeto dinámico:**

1. Haga clic con el botón derecho en cualquier elemento secundario de una **vista dinámica**.
1. Elija **Add Watch**. Se `object.name` convierte `((dynamic) object).name` y aparece en una nueva ventana **de Inspección.**

El depurador también agrega un nodo secundario **de vista dinámica** del objeto a la ventana **Automático.** Para abrir la ventana **Automático,** durante la depuración, seleccione **Depurar** > **autos de****Windows** > .

**La vista dinámica** también mejora la depuración de objetos COM. Cuando el depurador llega a un objeto COM ajustado en **System.__ComObject**, agrega un nodo **vista dinámica** para el objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observe una sola variable o expresión con QuickWatch

Puede utilizar **QuickWatch** para observar una sola variable.

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

Para observar `a` la variable,

1. Establezca un punto de interrupción en la línea `a = a + b;` .

1. Inicie la depuración. La ejecución se detiene en el punto de interrupción.

1. Seleccione la `a` variable en el código.

1. Seleccione **Depurar** > **inspección rápida**, pulse **Mayús**+**F9**o haga clic con el botón derecho y seleccione **Inspección rápida**.

   Aparece el cuadro de diálogo **Inspección rápida.** La `a` variable se encuentra en el cuadro **Expresión** con un **valor** de **1**.

   ![Variable QuickWatch](../debugger/media/quickwatchvariable.png "Variable QuickWatch")

1. Para evaluar una expresión mediante la variable, escriba una expresión como `a + b` en el cuadro **Expresión** y seleccione **Reevaluar**.

   ![Expresión de QuickWatch](../debugger/media/quickwatchexpression.png "Expresión de QuickWatch")

1. Para agregar la variable o expresión de **Inspección rápida** a la ventana **Inspección,** seleccione **Agregar inspección**.

1. Seleccione **Cerrar** para cerrar la ventana **Inspección rápida.** (**QuickWatch** es un cuadro de diálogo modal, por lo que no puede continuar la depuración mientras esté abierto.)

1. Continúe la depuración. Puede observar la variable en la ventana **Inspección.**

## <a name="see-also"></a>Consulte también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primero mire la depuración](../debugger/debugger-feature-tour.md)
- [Ventanas del depurador](../debugger/debugger-windows.md)
