---
title: Establece una inspección en las Variables de Visual Studio | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 04/04/2017
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
ms.openlocfilehash: 187c9e682877a0f0633e7d3210454d40cae9de0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Establece una inspección en Variables mediante la inspección y las ventanas de inspección rápida en Visual Studio
Durante la depuración, puede usar el **inspección** y **Inspección rápida** windows para observar las variables y expresiones.  La diferencia es que la ventana **Inspección** puede mostrar varias variables, mientras que la ventana **Inspección rápida** muestra las variables de una en una. 

Las ventanas sólo están disponibles durante una sesión de depuración. Para abrir el **inspección** ventana, elija **Depurar > Windows > inspección > inspección (1, 2, 3, 4)**). Para abrir el **Inspección rápida** ventana, haga doble clic en la variable y elija **Inspección rápida** o elija **Depurar > Inspección rápida**.
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Observación de una única variable en Inspección rápida  
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
  
 Puede observar una variable en la ventana Inspección rápida como se indica a continuación:  
  
1.  Establezca un punto de interrupción en la línea `a = a + b;` .  
  
2.  Inicie la depuración. La ejecución se detiene en el punto de interrupción.  
  
3.  Abra la **Inspección rápida** ventana (haga doble clic en `a`, a continuación, elija **Inspección rápida**, o seleccione `a` y presione **MAYÚS+F9**).

    Debería ver una variable en el **valores** ventana, con un valor de 1.

    ![Expresión de inspección rápida](../debugger/media/watchexpression.png "QuickWatchExpression")  

    Si va a evaluar una expresión que emplea la variable, como agregar una expresión `a + b` a la **expresión** ventana y haga clic en **actualizar**. 
  
4.  Agregue la variable a la **inspección** ventana desde **Inspección rápida** haciendo clic en **Agregar inspección**. 

    > [!NOTE]
    > El **Inspección rápida** ventana es una ventana de cuadro de diálogo modal, por lo que no se puede continuar con la depuración mientras está abierto.  
  
5.  Cierre la ventana **Inspección rápida** . Ahora puede continuar con la depuración mientras observa el valor en la ventana **Inspección** .  
  
## <a name="observing-variables-with-the-watch-window"></a>Observación de las variables con la ventana Inspección  
 Puede observar varias variables con la ventana **Inspección** . Por ejemplo, si tiene el siguiente código:  
  
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
  
 Agregue los valores de las tres variables a la ventana Inspección como se muestra a continuación:  
  
1.  Establezca un punto de interrupción en la línea `c = a + b;` .  
  
2.  Inicie la depuración (**F5**) La ejecución se detiene en el punto de interrupción.  
  
3.  Abra la ventana Inspección (**Depurar > Windows > inspección > Inspección 1**, o **CTRL + ALT + W, 1**).  
  
4.  Agregue la variable `a` a la primera fila, la variable `b` a la segunda fila y la variable `c` a la tercera fila.

    Puede agregar variables haciendo clic en una fila vacía y escriba el nombre de variable.
  
5.  Continuar con la depuración (presione **F11** para avanzar el depurador).  
  
 Debería ver los cambios en los valores de variable durante la iteración en el bucle `for` .  
  
 Si está programando en código nativo, a veces puede ser necesario calificar el contexto de un nombre de variable o una expresión que contiene un nombre de variable. El contexto es la función, el archivo de código fuente y el módulo donde se encuentra una variable. Si es necesario calificar el contexto, puede usar la sintaxis del operador de contexto. Para obtener más información, vea [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
## <a name="observing-expressions-with-the-watch-window"></a>Observación de expresiones con la ventana Inspección  
 Ahora probemos usando una expresión en su lugar. Puede agregar cualquier expresión válida reconocida por el depurador.  
  
 Por ejemplo, si el código aparece en la sección anterior, puede obtener el promedio de los tres valores como se indica a continuación:  
  
 ![Expresión de inspección](../debugger/media/watchexpression.png "WatchExpression")  
  
 En general, las reglas de evaluación de expresiones de la ventana **Inspección** son las mismas que las reglas de evaluación de expresiones en el lenguaje de programación. Si la expresión tiene un error de sintaxis, puede esperar el mismo error del compilador que se produciría en el editor de código. Por ejemplo:  
  
 ![Error de la expresión de inspección](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Actualizar valores de Inspección que no están actualizados  
 En determinadas circunstancias, podría ver un icono de actualización (una flecha circular) cuando se evalúa una expresión en el **inspección** ventana.  Por ejemplo, si tiene desactivada la evaluación de propiedad (**Herramientas > Opciones > depuración > Habilitar evaluación de propiedades y otras llamadas a función implícitas**), y tiene el siguiente código:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Si establece una inspección en la propiedad `Count` de la lista, debería ver algo parecido a lo siguiente:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 La ilustración anterior muestra un error o un valor que no está actualizado. Por lo general, puede actualizar el valor haciendo clic en el icono, pero en algunos casos es preferible no actualizarlo. En primer lugar necesitará saber por qué no se evaluó el valor.  
  
 Si señala al icono, una información sobre herramientas proporciona información sobre el motivo por el que no se evaluó la expresión.  Si las flechas en círculo aparecen, la expresión no se evaluó por una de las siguientes razones:  
  
-   Se produjo un error cuando se evaluaba la expresión. Por ejemplo, debido a que se produjo un tiempo de espera o a que una variable estaba fuera del ámbito.  
  
-   La expresión contiene una llamada de función, que puede desencadenar un efecto secundario de la aplicación (consulte [expresiones y efectos secundarios](#bkmk_sideEffects)).  
  
-   Está desactivada la evaluación automática de propiedades y llamadas a funciones implícitas del depurador (**Herramientas > Opciones > depuración > Habilitar evaluación de propiedades y otras llamadas a función implícitas**), y, a continuación, la expresión no puede ser evalúa automáticamente.  
  
 Para actualizar el valor, haga clic en el icono de actualización o presione la barra espaciadora. El depurador intenta evaluar de nuevo la expresión. Si el icono de actualización aparece porque está desactivada la evaluación automática de propiedades y otras llamadas a función implícitas, se puede evaluar la expresión.  
  
 Si aparece un icono en forma de círculo con dos líneas onduladas que parecen hilos, la expresión no se evaluó debido a la dependencia potencial entre subprocesos. En otras palabras, la evaluación de código requiere ejecutar temporalmente otros subprocesos en la aplicación. Cuando se está en modo de interrupción, lo normal es que se detengan todos los subprocesos de la aplicación. Permitir que otros subprocesos se ejecuten temporalmente puede tener efectos inesperados en el estado de su programa y hacer que el depurador omita algunos eventos, como los puntos de interrupción o las excepciones de dichos subprocesos.  
  
##  <a name="bkmk_sideEffects"></a> Side Effects and Expressions  
 La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otra forma al estado del programa. Por ejemplo, la evaluación de la siguiente expresión cambia el valor de `var1`:  
  
```  
var1 = var2  
```  
  
 Este código puede producir una [efecto secundario](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Los efectos secundarios pueden dificultar la depuración al cambiar la forma en que funciona su programa.  
  
 Una expresión que se sabe que tienen efectos secundarios se evalúa sólo una vez, cuando se escriben por primera vez. Las evaluaciones subsiguientes están deshabilitadas. Para invalidar este comportamiento manualmente, haga clic en el icono de actualización que aparece junto al valor.  
  
 Una manera de evitar todos los efectos secundarios es desactivar la evaluación de función automática (**Herramientas > Opciones > depuración > Habilitar evaluación de propiedades y otras llamadas a función implícitas**).  
  
 Cuando se desactiva la evaluación de propiedades o las llamadas a funciones implícitas, puede forzar la evaluación mediante el modificador de formato **ac** (solo en C#). Vea [Format Specifiers in C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="bkmk_objectIds"></a> Uso de los identificadores de objeto en la ventana Inspección (C# y Visual Basic)  

 Hay ocasiones cuando desee observar el comportamiento de un objeto específico. Por ejemplo, puede realizar un seguimiento de un objeto que hace referencia a una variable local después de esa variable se ha salido del ámbito. En C# y Visual Basic, puede crear identificadores de objetos para instancias específicas de tipos y usarlos en la ventana Inspección y en condiciones de interrupción. Los servicios de depuración de Common Language Runtime (CLR) generan el identificador de objeto y lo asocian al objeto.  
  
> [!NOTE]
>  Los identificadores de objeto crean referencias débiles y no impiden que el objeto se recopile en la recolección de elementos no utilizados. Los identificadores de objeto solo son válidos para la sesión de depuración actual.  
  
 En el código siguiente, se crea un método un `Person` usando una variable local, pero desea saber cuál es el `Person`del nombre está en un método diferente:  
  
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
    List<Person> _people = new List<Person>();  
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
  
1.  Establezca un punto de interrupción en el código después de que se haya creado el objeto.  
  
2.  Inicie la depuración y, cuando se detenga la ejecución en el punto de interrupción, busque la variable en la ventana **Variables locales** , haga clic en la variable y seleccione **Crear el identificador del objeto**.  
  
3.  Debería ver un **$** junto con un número en el **locales** ventana, que representa el identificador de objeto.  
  
4.  Agregue el identificador de objeto a la ventana Inspección.  
  
5.  Establecer un punto de interrupción donde desee observar el comportamiento del objeto.  En el código anterior, estaría en el `DoSomething()` método.  
  
6.  Continúe con la depuración y, cuando la ejecución se detenga en el método `DoSomething()` , la ventana **Inspección** mostrará el objeto `Person` .  
  
> [!NOTE]
>  Si desea ver las propiedades del objeto, como `Person.Name` en el ejemplo anterior, debe haber habilitado la evaluación de propiedades.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Uso de registros en la ventana Inspección (solo en C++)  
 Si depura código nativo, puede agregar nombres de registro así como nombres de variable mediante  **$ \<registrar nombre >** o  **@ \<registrar nombre >**.  Para obtener más información, consulta [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamic-view-and-the-watch-window"></a>Vista dinámica y la ventana Inspección  
 Algunos lenguajes de secuencias de comandos (por ejemplo, JavaScript o Python) usan dynamic o [duck escribiendo](https://en.wikipedia.org/wiki/Duck_typing), y los lenguajes .NET (versión 4.0 y versiones posterior) admiten objetos que son difíciles de observar con las ventanas de depuración normales, ya que puede tener propiedades en tiempo de ejecución y métodos que no se puede mostrar.  
  
 Cuando la ventana Inspección muestra un objeto creado a partir de un tipo que implementa el [interfaz IDynamicMetaObjectProvider](/dotnet/api/system.dynamic.idynamicmetaobjectprovider?view=netframework-4.7), el depurador agrega una clase especial **vista dinámica** nodo para el **automático**  mostrar. Este nodo muestra los miembros dinámicos del objeto dinámico, pero no permite editar los valores del miembro.  
  
 Si hace clic con el botón derecho en cualquier elemento secundario de una **vista dinámica** y elige **Agregar inspección**, el depurador inserta una nueva variable de inspección que convierte el objeto en un objeto dinámico. En otras palabras, **object Name** pasa a ser (**(dynamic)object).Name**.  
  
 La evaluación de los miembros de una **vista dinámica** puede tener efectos secundarios. Para obtener una explicación de los efectos secundarios, vea [Side Effects and Expressions](#bkmk_sideEffects). En C#, el depurador no vuelve a evaluar automáticamente los valores mostrados en la **Vista dinámica** cuando se pasa a una nueva línea de código. En Visual Basic, las expresiones agregadas a través de la **vista dinámica** se actualizan automáticamente.  
  
 Para obtener instrucciones sobre cómo actualizar los valores de Vista dinámica, vea [Actualizar valores de Inspección que no están actualizados](#bkmk_refreshWatch).  
  
 Si desea mostrar solo la **Vista dinámica** para un objeto, puede usar el especificador de formato **dinámico** :  
  
-   C#: **ObjectName, dynamic**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 La **Vista dinámica** también mejora la experiencia de depuración para los objetos COM. Cuando el depurador encuentra un objeto COM ajustado en **System.__ComObject**, agrega un nodo **Vista dinámica** para el objeto.  
  
## <a name="see-also"></a>Vea también  
 [Ventanas del depurador](../debugger/debugger-windows.md)
