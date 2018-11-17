---
title: Establece una inspección en variables en Visual Studio | Microsoft Docs
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
ms.openlocfilehash: aa469b109e0e22e426d76f75be50309196c6a264
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826796"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Variables de inspección con ventanas Inspección e Inspección rápida 

Durante la depuración, puede usar **inspección** windows y **Inspección rápida** para observar las variables y expresiones. Windows solo están disponibles durante una sesión de depuración.

**Inspección** windows pueden mostrar varias variables a la vez durante la depuración. El **Inspección rápida** cuadro de diálogo muestra una única variable a la vez y debe cerrarse para que pueda continuar la depuración.

## <a name="observe-variables-with-a-watch-window"></a>Observar variables con una ventana Inspección

Puede abrir más de un **inspección** ventana y observe más de una variable en un **inspección** ventana. 

Por ejemplo, para establecer una inspección de los valores de `a`, `b`, y `c` en el código siguiente:

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

1. Establecer un punto de interrupción en el `c = a + b;` línea haciendo clic en el margen izquierdo, seleccione **depurar** > **Alternar puntos de interrupción**, o presionando **F9**.
   
1. Iniciar la depuración seleccionando el verde **iniciar** flecha o **depurar** > **Iniciar depuración**, o bien presione **F5**. La ejecución se detiene en el punto de interrupción.
   
1. Abra un **inspección** ventana seleccionando **depurar** > **Windows** > **inspección**  >   **Inspección 1**, o presionando **Ctrl**+**Alt**+**W** > **1**.
   
   Puede abrir adicionales **inspección** windows seleccionando windows **2**, **3**, o **4**.
   
1. En el **inspección** ventana, seleccione una fila vacía y variable de tipo `a`. Lo mismo para `b` y `c`.
   
   ![Ver las variables](../debugger/media/watchvariables.png "WatchVariables")
   
1. Continuar con la depuración seleccionando **depurar** > **paso a paso** o presionando **F11** según sea necesario para avanzar. Los valores de la variable en el **inspección** ventana Cambiar a medida que recorre el `for` bucle.
   
>[!NOTE]
>Sólo, para C++ 
>- Es posible que deba calificar el contexto de un nombre de variable o una expresión que utiliza un nombre de variable. El contexto es la función, archivo de código fuente o módulo donde se encuentra una variable. Si es necesario calificar el contexto, use el [operador de contexto (C++)](../debugger/context-operator-cpp.md) sintaxis en el **nombre** en el **inspección** ventana. 
>  
>- Puede agregar nombres de registro y nombres de variable mediante  **$ \<registrar&nbsp;nombre >** o  **@ \<registrar&nbsp;nombre >** a la **nombre** en el **inspección** ventana. Para obtener más información, consulta [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usar expresiones en una ventana Inspección

Puede observar cualquier expresión válida reconocida por el depurador en un **inspección** ventana.

Por ejemplo, para el código en la sección anterior, puede obtener el promedio de los tres valores escribiendo `(a + b + c) / 3` en el **inspección** ventana:

![Expresión de inspección](../debugger/media/watchexpression.png "expresión de inspección")

Las reglas de evaluación de expresiones en el **inspección** ventana generalmente son las mismas que las reglas de evaluación de expresiones en el lenguaje de código. Si una expresión tiene un error de sintaxis, esperar a que el mismo error del compilador como se muestra en el editor de código. Por ejemplo, un error de escritura en la expresión anterior produce este error en la **inspección** ventana:

![Vea el error de expresión](../debugger/media/watchexpressionerror.png "Ver error de expresión")

Puede aparecer un círculo con icono de dos líneas onduladas en los **inspección** ventana. Este icono significa que el depurador no evalúa la expresión debido a la dependencia potencial entre subprocesos. Evaluar el código requiere otros subprocesos en la aplicación se ejecute temporalmente, pero dado que está en modo de interrupción, normalmente se detienen todos los subprocesos de la aplicación. Permitir que otros subprocesos se ejecuten temporalmente puede tener efectos inesperados en el estado de la aplicación y del depurador que omita algunos eventos, como los puntos de interrupción y excepciones en esos subprocesos.

### <a name="bkmk_refreshWatch"></a> Actualizar valores de comprobación

Podría aparecer un icono de actualización (flecha circular) en el **inspección** ventana cuando se evalúa una expresión. El icono de actualización indica un error o un valor que no está actualizado. 

Para actualizar el valor, seleccione el icono de actualización, o presione la barra espaciadora. El depurador intenta evaluar de nuevo la expresión. Sin embargo, no es posible que desee o poder volver a evaluar la expresión, dependiendo de por qué no se evalúa el valor. 

Mantenga el mouse sobre el icono de actualización o vea el **valor** columna por la razón no se puede evaluar la expresión. Entre los motivos se incluyen:

- Se produjo un error como se evaluaba la expresión, como se muestra en el ejemplo anterior. Podría producirse un tiempo de espera, o podría ser una variable fuera del ámbito.
  
- La expresión tiene una llamada de función que podría desencadenar un efecto secundario en la aplicación. Consulte [expresión efectos](#bkmk_sideEffects).
  
- Se deshabilitó la evaluación automática de propiedades y llamadas a función implícitas. 
  
Si el icono de actualización aparece porque se deshabilitó la evaluación automática de propiedades y llamadas a función implícitas, puede habilitarlo seleccionando **Habilitar evaluación de propiedades y otras llamadas a función implícitas** en **herramientas**   >  **Opciones** > **depuración** > **General**.

Para que se muestra cómo usar el icono de actualización:

1. En **herramientas** > **opciones** > **depuración** > **General**, desactive la **Habilitar evaluación de propiedades y otras llamadas a función implícitas** casilla de verificación. 
   
1. Escriba el siguiente código y en el **inspección** ventana, Establece una inspección en el `list.Count` propiedad. 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. Inicie la depuración. El **inspección** ventana muestra algo como el siguiente mensaje:
   
   ![Actualizar inspección](../debugger/media/refreshwatch.png "actualizar inspección")
   
1. Para actualizar el valor, seleccione el icono de actualización, o presione la barra espaciadora. El depurador vuelve a evaluar la expresión. 

### <a name="bkmk_sideEffects"></a> Efectos de expresión 

Evaluación de algunas expresiones puede cambiar el valor de una variable o afectar el estado de la aplicación. Por ejemplo, la evaluación de la siguiente expresión cambia el valor de `var1`:

```csharp
var1 = var2
```

Este código puede provocar un [efecto](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efectos secundarios pueden dificultar la depuración más cambiando la forma en que funciona su aplicación.

Una expresión con efectos secundarios se evalúa solo una vez, cuando se escriben por primera vez. Después de eso, la expresión aparece atenuada en el **inspección** ventana y aún más evaluaciones están deshabilitados. La información sobre herramientas o **valor** columna explica que la expresión que produce un efecto secundario. Puede forzar una nueva evaluación seleccionando el icono de actualización que aparece junto al valor.

Una manera de evitar la designación de efectos secundarios es desactivar la evaluación de función automática. En **herramientas** > **opciones** > **depuración** > **General**, anule la selección de **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

Para C# solo, cuando se desactiva la evaluación de propiedades o llamadas a función implícitas, puede forzar la evaluación mediante la adición de la **ac** modificador de formato a una variable **nombre** en el **inspección**  ventana. Consulte [especificadores en C# de formato](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Usar identificadores de objeto en la ventana Inspección (C# y Visual Basic)

A veces desea observar el comportamiento de un objeto específico. Por ejemplo, es posible que desee realizar un seguimiento de un objeto al que hace referencia una variable local después de esa variable se ha salido del ámbito. En C# y Visual Basic, puede crear identificadores de objeto para instancias específicas de tipos de referencia y usarlas en el **inspección** ventana y en condiciones de interrupción. El identificador de objeto es generado por los servicios de depuración de common language runtime (CLR) y asociado al objeto.

> [!NOTE]
> Los identificadores de objeto crean referencias débiles que no impiden el objeto recolectado. Los identificadores de objeto solo son válidos para la sesión de depuración actual.

En el código siguiente, la `MakePerson()` método crea un `Person` utilizando una variable local: 

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

Para averiguar el nombre de la `Person` en el `DoSomething()` método, puede agregar una referencia a la `Person` Id. de objeto en el **inspección** ventana.

1. Establezca un punto de interrupción en el código después de la `Person` se ha creado el objeto.
   
1. Inicie la depuración.
   
1. Cuando se detiene la ejecución en el punto de interrupción, abra el **variables locales** ventana eligiendo **depurar** > **Windows** > **devariableslocales**.
   
1. En el **variables locales** ventana, haga clic en el `Person` variable y seleccione **Make Object ID**.
   
   Debería ver un signo de dólar (**$**) junto con un número en el **variables locales** ventana, que es el identificador de objeto.
   
1. Agregue el identificador de objeto para el **inspección** ventana haciendo clic en el identificador de objeto y seleccionar **Agregar inspección**.
   
1. Establecer otro punto de interrupción en el `DoSomething()` método.
   
1. Continúe la depuración. Cuando la ejecución se detiene en el `DoSomething()` método, el **inspección** ventana muestra el `Person` objeto.
   
   > [!NOTE]
   > Si desea ver las propiedades del objeto, como `Person.Name`, debe habilitar evaluación de propiedades seleccionando **herramientas** > **opciones**  >   **Depuración** > **General** > **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

## <a name="dynamic-view-and-the-watch-window"></a>Vista dinámica y la ventana Inspección

Algunos lenguajes de scripting (por ejemplo, JavaScript o Python) usan dynamic o [duck](https://en.wikipedia.org/wiki/Duck_typing) escribiendo y .NET 4.0 y versiones posteriores admite objetos que son difíciles de observar en las ventanas de depuración normales.

El **inspección** ventana muestra estos objetos como objetos dinámicos, que se crean a partir de los tipos que implementan la <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaz. Los nodos del objeto dinámico muestran a los miembros dinámicos de los objetos dinámicos, pero no permiten la edición de los valores de miembro. 

Para actualizar **vista dinámica** valores, seleccionados el [icono de actualización](#bkmk_refreshWatch) situado junto al nodo de objeto dinámico. 

Para mostrar solamente el **vista dinámica** para un objeto, agregue un **dinámica** especificador de formato después del nombre del objeto dinámico en el **inspección** ventana:

- Para C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- El C# depurador no vuelve a evaluar los valores de forma automática el **vista dinámica** cuando se pasa a la siguiente línea de código. 
>- El depurador de Visual Basic actualiza automáticamente las expresiones agregadas a través de la **vista dinámica**.
>- Evaluación de los miembros de un **vista dinámica** puede tener [efectos](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). 

**Para insertar una nueva inspección variable convierte el objeto en un objeto dinámico:**
  
1. Haga clic en cualquier elemento secundario de un **vista dinámica**.
1. Elija **Agregar inspección**. El `object.name` se convierte en `((dynamic) object).name` y aparece en una nueva **inspección** ventana.

El depurador también agrega un **vista dinámica** nodo secundario del objeto para el **automático** ventana. Para abrir el **automático** ventana, durante la depuración, seleccione **depurar** > **Windows** > **automático**. 

**Vista dinámica** también mejora la depuración para los objetos COM. Cuando el depurador obtiene un objeto COM ajustado en **System.__ComObject**, agrega un **vista dinámica** nodo para el objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observe una sola variable o expresión en Inspección rápida

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

Para observar el `a` variable, 
   
1. Establezca un punto de interrupción en la línea `a = a + b;` .
   
1. Inicie la depuración. La ejecución se detiene en el punto de interrupción.
   
1. Seleccione la variable `a` en el código.
   
1. Seleccione **depurar** > **Inspección rápida**, presione **MAYÚS**+**F9**, o haga clic en y seleccione **Inspección rápida**. 
   
   El **Inspección rápida** aparece el cuadro de diálogo. El `a` variable está en el **expresión** cuadro con un **valor** de **1**.
   
   ![Variable de inspección rápida](../debugger/media/quickwatchvariable.png "variable de inspección rápida")
   
1. Para evaluar una expresión que usa la variable, escriba una expresión como `a + b` en el **expresión** cuadro y seleccione **volver a evaluar**.
   
   ![Expresión de inspección rápida](../debugger/media/quickwatchexpression.png "expresión de inspección rápida")
   
1. Para agregar la variable o expresión de **Inspección rápida** a la **inspección** ventana, seleccione **Agregar inspección**.
   
1. Seleccione **cerrar** para cerrar el **Inspección rápida** ventana. (**Inspección rápida** es un cuadro de diálogo modal, por lo que no puede continuar la depuración mientras está abierto.)
   
1. Continúe la depuración. Puede observar la variable en el **inspección** ventana.

## <a name="see-also"></a>Vea también
 [¿Qué es la depuración?](../debugger/what-is-debugging.md)  
 [Escribir mejor C# código con Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Primer vistazo al depurar](../debugger/debugger-feature-tour.md) [ventanas del depurador](../debugger/debugger-windows.md)
