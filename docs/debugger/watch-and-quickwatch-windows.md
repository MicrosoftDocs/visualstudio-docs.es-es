---
title: Establece una inspección en Variables en Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325021"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Establece una inspección en variables mediante las ventanas inspección e inspección rápida en Visual Studio

Durante la depuración, puede usar el **inspección** y **Inspección rápida** para observar las variables y expresiones.  La diferencia es que la ventana **Inspección** puede mostrar varias variables, mientras que la ventana **Inspección rápida** muestra las variables de una en una.

Windows solo están disponibles durante una sesión de depuración. Para abrir el **inspección** ventana, elija **depurar** > **Windows** > **inspección**y, a continuación, elija **Inspección 1**, **inspección 2**, **inspección 3**, o **inspección 4**. Para abrir el **Inspección rápida** ventana, haga clic en la variable y elija **Inspección rápida**, o elija simplemente **depurar** > **Inspección rápida** .

## <a name="observe-variables-with-the-watch-window"></a>Observar variables con la ventana Inspección

Puede observar más de una variable con el **inspección** ventana. Por ejemplo, si tiene el siguiente código:

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

Agregue los valores de las tres variables para el **inspección** ventana como sigue:

1. Seleccione el `c = a + b;` línea.

2. Establezca un punto de interrupción (eligiendo **depurar** > **Alternar puntos de interrupción** o presione F9).

3. Inicie la depuración (F5). La ejecución se detiene en el punto de interrupción.

4. Abra el **inspección** ventana (eligiendo **depurar** > **Windows** > **inspección**  >   **Inspección 1**, o presione Ctrl + Alt + W, 1).

5. Seleccione una fila vacía y escriba la variable `a`. A continuación, hacer lo mismo para las variables `b` y `c`.

   ![Ver las variables](../debugger/media/watchvariables.png "WatchVariables")

6. Continuar con la depuración presionando F11 según sea necesario para avanzar al depurador.

Debería ver los cambios en los valores de variable durante la iteración en el bucle `for` .

Si está programando en código nativo, a veces puede ser necesario calificar el contexto de un nombre de variable o una expresión que tiene un nombre de variable. El contexto es la función, el archivo de código fuente y el módulo donde se encuentra una variable. Si es necesario calificar el contexto, puede usar la sintaxis del operador de contexto. Para obtener más información, consulte [operador de contexto (C++)](../debugger/context-operator-cpp.md).

## <a name="observe-expressions-with-the-watch-window"></a>Observe las expresiones con la ventana Inspección

Ahora probemos usando una expresión en su lugar. Puede agregar cualquier expresión válida reconocida por el depurador.

Por ejemplo, si tiene el código que aparece en la sección anterior, puede obtener el promedio de los tres valores mediante el uso de esta expresión:

![Expresión de inspección](../debugger/media/watchexpression.png "WatchExpression")

Las reglas de evaluación de expresiones en el **inspección** ventana generalmente son las mismas que las reglas de evaluación de expresiones en el lenguaje de programación. Si la expresión tiene un error de sintaxis, esperar a que el mismo error del compilador que ve en el editor de código. Por ejemplo:

![Vea el error de expresión](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> Actualizar valores de inspección que no están actualizados

Es posible que aparezca un icono de actualización (una flecha circular) cuando se evalúa una expresión en el **inspección** ventana. Si ha desactivado la evaluación de propiedades (eligiendo **herramientas** > **opciones** > **depuración**  >   **General**, a continuación, borrar **Habilitar evaluación de propiedades y otras llamadas a función implícitas**), y que ha escrito el código siguiente:

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

Debería ver algo parecido a la siguiente imagen si establece una inspección en el `Count` propiedad de la lista:

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

La ilustración anterior muestra un error o un valor que no está actualizado. Por lo general, puede actualizar el valor seleccionando el icono, pero en algunos casos es preferible no actualizarlo. En primer lugar deberá saber por qué no se evalúa el valor.

Información sobre herramientas proporciona información sobre por qué no se puede evaluar la expresión si señala al icono. Si las flechas en círculo aparecen, la expresión no se evalúa para uno de los siguientes motivos:

- Se produjo un error cuando se evaluaba la expresión. Por ejemplo, debido a que se produjo un tiempo de espera o a que una variable estaba fuera del ámbito.

- La expresión tiene una llamada de función, lo que podría desencadenar un efecto secundario de la aplicación (consulte la [efectos y expresiones](#bkmk_sideEffects) sección).

- Ha desactivado la evaluación automática de propiedades y llamadas función implícitas del depurador (eligiendo **herramientas** > **opciones** > **dedepuración**  >  **General**, a continuación, borrar **Habilitar evaluación de propiedades y otras llamadas a función implícitas**). No se puede evaluar la expresión automáticamente, a continuación.

Para actualizar el valor, seleccione el icono de actualización, o presione la barra espaciadora. El depurador intenta evaluar de nuevo la expresión. Puede aparecer el icono de actualización porque se ha desactivado la evaluación automática de propiedades y otras llamadas a función implícitas. En este caso, el depurador puede evaluar la expresión.

Puede aparecer un icono que es un círculo con dos líneas onduladas que parecen subprocesos. Este icono significa que el depurador no evalúa la expresión debido a la dependencia potencial entre subprocesos. En otras palabras, la evaluación de código requiere ejecutar temporalmente otros subprocesos en la aplicación. Cuando se está en modo de interrupción, lo normal es que se detengan todos los subprocesos de la aplicación. Permitir que otros subprocesos se ejecuten temporalmente puede tener efectos inesperados en el estado de su programa y hacer que el depurador omita algunos eventos, como los puntos de interrupción o las excepciones de dichos subprocesos.

## <a name="bkmk_sideEffects"></a> Efectos secundarios y expresiones

La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otra forma al estado del programa. Por ejemplo, la evaluación de la siguiente expresión cambia el valor de `var1`:

```csharp
var1 = var2
```

Este código puede provocar un [efecto](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden dificultar la depuración al cambiar la forma en que funciona su programa.

Una expresión que se sabe que tienen efectos secundarios se evalúa solo una vez, cuando se escriben por primera vez. Más evaluaciones están deshabilitadas. Puede invalidar este comportamiento manualmente, seleccione el icono de actualización que aparece junto al valor.

Una forma de evitar todos los efectos secundarios es desactivar la evaluación de función automática (eligiendo **herramientas** > **opciones** > **depuración**  >  **General**, a continuación, borrar **Habilitar evaluación de propiedades y otras llamadas a función implícitas**).

Cuando se desactiva la evaluación de propiedades o las llamadas a funciones implícitas, puede forzar la evaluación mediante el modificador de formato **ac** (solo en C#). Consulte [especificadores en C# de formato](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Usar identificadores de objeto en la ventana Inspección (C# y Visual Basic)

En ocasiones desee observar el comportamiento de un objeto específico. Por ejemplo, es posible que desee realizar un seguimiento de un objeto al que hace referencia una variable local después de esa variable se ha salido del ámbito. En C# y Visual Basic, puede crear identificadores de objeto para instancias específicas de tipos de referencia y usarlas en el **inspección** ventana y en condiciones de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles que no impiden el objeto recolectado. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

En el código siguiente, se crea un método un `Person` usar una variable local, pero desea saber cuál es el `Person`del nombre está en un método diferente:

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

Puede agregar una referencia a dicho objeto `Person` en la ventana **Inspección** tal como sigue:

1. Seleccione una línea en el código que se produce que el objeto se ha creado.

2. Establezca un punto de interrupción (eligiendo **depurar** > **Alternar puntos de interrupción** o presione F9).

3. Inicie la depuración.

4. Cuando la ejecución se detiene en el punto de interrupción, abra el **variables locales** ventana (eligiendo **depurar** > **Windows** > **devariableslocales**), haga clic en la variable y seleccione **Make Object ID**.

   Debería ver un signo de dólar (**$**) junto con un número en el **variables locales** ventana, que es el identificador de objeto.

   > [!NOTE]
   > Si desea ver las propiedades del objeto, como `Person.Name`, debe habilitar evaluación de propiedades seleccionando **herramientas** > **opciones**  >   **Depuración** > **General**, a continuación, estableciendo **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

5. Agregue el identificador de objeto para el **inspección** ventana, con el botón secundario en el signo de dólar y el número y luego elija **Agregar inspección**.

6. Establezca un punto de interrupción donde desee observar el comportamiento del objeto.  En el código anterior, estaría en el `DoSomething()` método.

7. Continúe la depuración. Cuando se detenga la ejecución en el `DoSomething()` método, el **inspección** ventana muestra el `Person` objeto.

## <a name="use-registers-in-the-watch-window-c-only"></a>Usar registros en la ventana Inspección (solo C++)

Puede agregar nombres de registro y nombres de variable mediante  **$ \<registrar&nbsp;nombre >** o  **@ \<registrar&nbsp;nombre >** mientras se depura código nativo. Para obtener más información, consulta [Pseudovariables](../debugger/pseudovariables.md).

## <a name="dynamic-view-and-the-watch-window"></a>Vista dinámica y la ventana Inspección

Algunos lenguajes de scripting (por ejemplo, JavaScript o Python) usan dynamic o [pato](https://en.wikipedia.org/wiki/Duck_typing), y los lenguajes .NET (versión 4.0 y versiones posterior) admiten objetos que son difíciles de observar con las ventanas de depuración normales, ya que puede tener propiedades de tiempo de ejecución y métodos que no se puede mostrar.

El **inspección** ventana puede mostrar un objeto dinámico, que se crea a partir de un tipo que implementa el <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaz. Cuando se muestre este objeto, el depurador agrega un especial **vista dinámica** nodo secundario del nombre del objeto si abre el **automático** ventana (eligiendo **depurar**  >  **Windows** > **automático**). Este nodo muestra a los miembros dinámicos del objeto dinámico, pero no permite la edición de los valores de miembro.

Para insertar una nueva inspección variable convierte el objeto en un objeto dinámico:

1. Haga clic en cualquier elemento secundario de un **vista dinámica**.
2. Elija **Agregar inspección**. A continuación, `object.name` se convierte en `((dynamic) object).name`.

La evaluación de los miembros de una **vista dinámica** puede tener efectos secundarios. Para obtener una explicación de los efectos secundarios, vea el [efectos y expresiones](#bkmk_sideEffects) sección. C#, el depurador no vuelve a evaluar automáticamente los valores mostrados en la **vista dinámica** cuando se pasa a una nueva línea de código. En Visual Basic, las expresiones agregadas a través de la **vista dinámica** se actualizan automáticamente.

Para obtener instrucciones sobre cómo actualizar el **vista dinámica** valores, vea el [valores de comprobación de actualización que no están actualizados](#bkmk_refreshWatch) sección.

Si desea mostrar solamente el **vista dinámica** para un objeto, puede usar el **dinámica** formato especificador en la **inspección** ventana:

- C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

La **Vista dinámica** también mejora la experiencia de depuración para los objetos COM. Cuando el depurador obtiene un objeto COM ajustado en **System.__ComObject**, agrega un **vista dinámica** nodo para el objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observe una sola variable o expresión en Inspección rápida

Puede usar la ventana **Inspección rápida** para observar una única variable. Por ejemplo, si tiene el siguiente código:

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

Puede observar una variable en el **Inspección rápida** ventana como sigue:

1. Establezca un punto de interrupción en la línea `a = a + b;` .

2. Inicie la depuración. La ejecución se detiene en el punto de interrupción.

3. Seleccione la variable `a`.

4. Elija **depurar** > **Inspección rápida** o presione **MAYÚS+F9**. El **Inspección rápida** aparecerá la ventana. En el **valor** cuadro, el `a` variable se muestra con un valor de 1.

   ![Variable de inspección rápida](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   Para evaluar una expresión que usa la variable, escriba una expresión como `a + b` a la **expresión** y haga clic en **volver a evaluar**.

   ![Expresión de inspección rápida](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   Para agregar la variable o expresión a la **inspección** ventana desde **Inspección rápida**, elija **Agregar inspección**.

   > [!NOTE]
   > El **Inspección rápida** es una ventana de cuadro de diálogo modal, por lo que no puede continuar la depuración mientras está abierto.

5. Cierre la ventana **Inspección rápida** . Ahora puede continuar con la depuración mientras observa el valor en la ventana **Inspección** .

## <a name="see-also"></a>Vea también

[Ventanas del depurador](../debugger/debugger-windows.md)
