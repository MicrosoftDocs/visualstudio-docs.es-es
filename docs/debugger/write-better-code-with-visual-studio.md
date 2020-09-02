---
title: Herramientas y técnicas de depuración
description: Para escribir código de mayor calidad y con menos errores, use Visual Studio, que le permitirá corregir excepciones y errores, y mejorar el código.
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89311396"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Herramientas y técnicas de depuración para ayudarle a escribir código de mayor calidad

Corregir errores y problemas en el código puede ser una tarea laboriosa y, en ocasiones, frustrante. Se tarda tiempo en aprender a depurarlo eficazmente, pero un IDE eficaz como Visual Studio puede facilitarle mucho el trabajo. Un IDE puede ayudarle a corregir los errores y depurar el código más rápidamente, y no solo eso, sino que también puede ayudarle a escribir código de mayor calidad y con menos errores. Nuestro objetivo en este artículo es proporcionarle una visión integral del proceso de corrección de errores para que sepa cuándo conviene usar el analizador de código y el depurador, cómo corregir las excepciones y cómo realizar la codificación para su intención. Si ya sabe que necesita usar el depurador, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

En este artículo, se hablará del uso del IDE para mejorar la productividad de las sesiones de codificación. Abordaremos varias tareas, como las siguientes:

* Preparación del código para la depuración aprovechando el analizador de código del IDE

* Procedimientos para corregir excepciones (errores en tiempo de ejecución)

* Procedimientos para minimizar los errores codificando la intención (mediante Assert)

* Cuándo usar el depurador

Para mostrar estas tareas, veremos algunos de los tipos de errores y problemas más comunes que encontrará al intentar depurar las aplicaciones. Aunque el código de ejemplo es C#, la información conceptual se aplica generalmente a C++, Visual Basic, JavaScript y otros lenguajes admitidos en Visual Studio, a menos que se indique lo contrario. Las capturas de pantalla son de código C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Creación de una aplicación de ejemplo con algunos errores y problemas

El código siguiente tiene algunos errores que puede corregir mediante el IDE de Visual Studio. La aplicación que presentamos es una aplicación sencilla que simula la obtención de datos JSON mediante alguna operación, la deserialización de datos en un objeto y la actualización de una lista simple con los datos nuevos.

Para crear la aplicación:

1. Debe tener instalado Visual Studio y las cargas de trabajo **Desarrollo multiplataforma de .NET Core** o **Desarrollo de escritorio de .NET**, según el tipo de aplicación que quiera crear.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en **Herramientas** > **Obtener herramientas y características**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** (o la carga de trabajo **Desarrollo de escritorio de .NET**) y, después, haga clic en **Modificar**.

1. Abra Visual Studio.

    ::: moniker range=">=vs-2019"
    En la ventana de inicio, elija **Crear un proyecto nuevo**. Escriba **consola** en el cuadro de búsqueda y, luego, **Aplicación de consola (.NET Core)** o **Aplicación de consola (.NET Framework)** . Seleccione **Siguiente**. Escriba un nombre de proyecto como, por ejemplo, **Console_Parse_JSON** y haga clic en **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **Aplicación de consola** y, luego, en el panel central, **Aplicación de consola (.NET Core)** o **Aplicación de consola (.NET Framework)** . Escriba un nombre como, por ejemplo, **Console_Parse_JSON** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)** o **Aplicación de consola (.NET Framework)** , vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** o **Desarrollo de escritorio de .NET** y, luego, **Modificar**.

    Visual Studio crea el proyecto de consola, con lo que aparece el Explorador de soluciones (en el panel derecho).

1. Reemplace el código predeterminado del archivo *Program.cs* del proyecto por el código de ejemplo siguiente.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Busque los subrayados ondulados de color rojo y verde.

Antes de intentar iniciar la aplicación de ejemplo y ejecutar el depurador, compruebe el código en el editor de código en busca de subrayados ondulados de color rojo y verde. Estos representan los errores y advertencias identificados mediante el analizador de código del IDE. Los subrayados ondulados de color rojo son errores en tiempo de compilación que debe corregir antes de poder ejecutar el código. Los subrayados ondulados de color verde son advertencias. Aunque a menudo se puede ejecutar la aplicación sin corregir las advertencias, estas pueden ser una fuente de errores y, a menudo, si se investigan, se ahorra tiempo y problemas. Estas advertencias y errores también se muestran en la ventana **Lista de errores**, si prefiere una vista de lista.

En la aplicación de ejemplo, verá varios subrayados ondulados de color rojo que debe corregir y uno verde. Este es el primer error.

![Error que muestra un subrayado ondulado de color rojo](../debugger/media/write-better-code-red-squiggle.png)

Para corregir este error, verá otra característica del IDE representada por el icono de bombilla.

## <a name="check-the-light-bulb"></a>Compruebe la bombilla.

El primer subrayado ondulado de color rojo representa un error en tiempo de compilación. Pase el puntero sobre él y verá el mensaje ```The name `Encoding` does not exist in the current context```.

Fíjese en que este error muestra un icono de bombilla hacia la parte inferior izquierda. Junto con el icono de destornillador ![icono de destornillador](../ide/media/screwdriver-icon.png), el icono de bombilla ![icono de bombilla](../ide/media/light-bulb-icon.png) representa acciones rápidas que pueden ayudarle a corregir o refactorizar el código insertado. La bombilla representa los problemas que *debe* corregir. El destornillador es para los problemas que puede elegir corregir. Use la primera corrección sugerida para resolver este error; para ello, haga clic en **using System.Text**, a mano izquierda.

![Uso de la bombilla para corregir el código](../debugger/media/write-better-code-missing-include.png)

Al hacer clic en este elemento, Visual Studio agrega la instrucción `using System.Text` en la parte superior del archivo *Program.cs* y desaparece el subrayado ondulado de color rojo. (Si no está seguro del resultado de aplicar una corrección sugerida, elija el vínculo **Vista previa de los cambios** a la derecha antes de hacerlo).

El anterior es un error común que normalmente se corrige agregando una nueva instrucción `using` al código. Hay varios errores comunes similares a este, como ```The type or namespace `Name` cannot be found.```. Estos tipos de errores pueden indicar que falta una referencia de ensamblado (haga clic con el botón derecho en el proyecto y haga clic en **Agregar** > **Referencia**), un nombre mal escrito o una biblioteca que falta y que debe agregar (para C#, haga clic con el botón derecho en el proyecto y, luego, seleccione **Administrar paquetes NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Corrección de los errores y advertencias restantes

Hay unos cuantos más subrayados ondulados en este código. Aquí se muestra un error común de conversión de tipo. Al pasar el puntero sobre el subrayado ondulado, verá que el código está intentando convertir una cadena en un valor int, que no se admite a menos que agregue código explícito para realizar la conversión.

![Error de la conversión de tipo](../debugger/media/write-better-code-conversion-error.png)

Dado que el analizador de código no puede adivinar su intención, en este caso no hay ninguna bombilla para ayudarle. Para corregir este error, debe conocer la intención del código. En este ejemplo, no es demasiado difícil ver que `points` debe ser un valor numérico (entero), ya que está intentando agregar `points` a `totalpoints`.

Para corregir este error, cambie el miembro `points` de la clase `User` de:

```csharp
[DataMember]
internal string points;
```

a:

```csharp
[DataMember]
internal int points;
```

Las líneas de subrayado ondulado de color rojo del editor de código desaparecen.

Después, mantenga el ratón sobre el subrayado ondulado de color verde en la declaración del miembro de datos `points`. El analizador de código le indica que nunca se le asignó un valor a la variable.

![Mensaje de advertencia de variable sin asignar](../debugger/media/write-better-code-warning-message.png)

Normalmente, esto representa un problema que debe corregirse. Sin embargo, en la aplicación de ejemplo se están almacenando datos en la variable `points` durante el proceso de deserialización y, después, se agrega ese valor al miembro de datos `totalpoints`. En este ejemplo, se conoce la intención del código y se puede omitir la advertencia de forma segura. Pero si quiere eliminar la advertencia, puede reemplazar el código siguiente:

```csharp
item.totalpoints = users[i].points;
```

por este:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

El subrayado ondulado de color verde desaparece.

## <a name="fix-an-exception"></a>Corrección de una excepción

Cuando haya corregido todos los subrayados ondulados de color rojo y resuelto (o al menos investigado) todos los subrayados ondulados de color verde, estará a punto para iniciar el depurador y ejecutar la aplicación.

Presione **F5** (**Depurar > Iniciar depuración**) o el botón **Iniciar depuración** ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas de depuración.

En este momento, la aplicación de ejemplo produce una excepción `SerializationException` (un error de tiempo de ejecución). Es decir, la aplicación retraerá los datos que está intentando serializar. Dado que inició la aplicación en modo de depuración (depurador adjunto), el ayudante de excepciones del depurador le llevará directamente al código que produjo la excepción y le proporcionará un mensaje de error útil.

![Excepción SerializationException](../debugger/media/write-better-code-serialization-exception.png)

El mensaje de error indica que el valor `4o` no se puede analizar como un entero. Por lo tanto, en este ejemplo, sabe que los datos son incorrectos: `4o` debe ser `40`. Sin embargo, si no tiene el control de los datos en un escenario real (por ejemplo, si los obtiene de un servicio web), ¿qué puede hacer? ¿Cómo lo arreglaría?

Cuando se alcanza una excepción, debe formular (y responder) un par de preguntas:

* ¿Esta excepción es solo un error que se puede corregir? O bien,

* ¿Es una excepción que se podrían encontrar los usuarios?

Si es la primera opción, corrija el error. (En la aplicación de ejemplo, eso implica corregir los datos incorrectos). Si es la segunda opción, puede que tenga que controlar la excepción en el código mediante un bloque `try/catch` (veremos otras estrategias posibles en la sección siguiente). En la aplicación de ejemplo, reemplace el código siguiente:

```csharp
users = ser.ReadObject(ms) as User[];
```

con este código:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Un bloque de `try/catch` presenta ciertos costos de rendimiento, por lo que solo querrá usarlo cuando realmente lo necesite, es decir, si (a) es posible que aparezca en la versión de lanzamiento de la aplicación, y si (b) la documentación del método indica que debe comprobar la excepción (suponiendo que la documentación se haya completado). En muchos casos, puede controlar una excepción adecuadamente, y el usuario nunca tendrá que tener conocimiento de ella.

A continuación se muestran un par de sugerencias importantes para el control de excepciones:

* Evite el uso de un bloque catch vacío, como `catch (Exception) {}`, que no realiza la acción adecuada para exponer o controlar un error. Un bloque catch vacío o no informativo puede ocultar excepciones y hacer que el código sea más difícil de depurar en lugar de más sencillo.

* Utilice el bloque `try/catch` en torno a la función específica que produce la excepción (`ReadObject`, en la aplicación de ejemplo). Si lo utiliza en un fragmento de código mayor, acabará ocultando la ubicación del error. Por ejemplo, no utilice el bloque `try/catch` en torno a la llamada a la función primaria `ReadToObject`, que se muestra aquí, ya que, de lo contrario, no sabrá exactamente dónde se produjo la excepción.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* En el caso de las funciones desconocidas que se incluyen en la aplicación, especialmente las que interactúan con datos externos (como una solicitud web), consulte la documentación para ver las excepciones que es probable que produzca la función. Puede tratarse de información crítica para un control de errores adecuado y para depurar la aplicación.

Para la aplicación de ejemplo, corrija `SerializationException` en el método `GetJsonData` cambiando `4o` a `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Aclaración de la intención del código mediante Assert

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús** + **F5**). Esto reiniciará la aplicación en menos pasos. Verá el resultado siguiente en la ventana de la consola:

![Valor NULL en la salida](../debugger/media/write-better-code-using-assert-null-output.png)

En esta salida se puede ver algo que no es correcto. Los valores **Name** y **LastName** del tercer registro están en blanco.

Este es un buen momento para hablar sobre una práctica de codificación útil, a menudo infrautilizada, que consiste en usar instrucciones `assert` en las funciones. Al agregar el código siguiente, se incluye una comprobación en tiempo de ejecución para asegurarse de que `firstname` y `lastname` no sean `null`. Reemplace el código siguiente en el método `UpdateRecords`:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

por este:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Al agregar instrucciones `assert` como esta a las funciones durante el proceso de desarrollo, puede ayudar a especificar la intención del código. En el ejemplo anterior, se especifica lo siguiente:

* Se requiere una cadena válida para el nombre.
* Se requiere una cadena válida para el apellido.

Al especificar la intención de esta manera, se aplican los requisitos. Se trata de un método sencillo y práctico que puede usar para exponer errores durante el desarrollo. (Las instrucciones `assert` también se usan como el elemento principal en las pruebas unitarias).

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús** + **F5**).

> [!NOTE]
> El código de `assert` solo está activo en una compilación de depuración.

Al reiniciar, el depurador se detiene en la instrucción `assert`, porque la expresión `users[i].firstname != null` se evalúa como `false` en lugar de como `true`.

![Resolución de Assert como "false"](../debugger/media/write-better-code-using-assert.png)

El error `assert` indica que hay un problema que se debe investigar. `assert` puede cubrir muchos escenarios en los que no es necesario ver una excepción. En este ejemplo, el usuario no verá ninguna excepción y se agregará un valor `null` como `firstname` en la lista de registros. Esto puede producir problemas más adelante (como se ve en la salida de la consola) y puede ser más difícil de depurar.

> [!NOTE]
> En escenarios en los que se llama a un método en el valor `null`, se produce `NullReferenceException` como resultado. Normalmente, se quiere evitar el uso de un bloque `try/catch` para una excepción general, es decir, una excepción que no está asociada a la función de biblioteca específica. Cualquier objeto puede producir `NullReferenceException`. Si no está seguro, consulte la documentación de la función de la biblioteca.

Durante el proceso de depuración, es conveniente mantener una determinada instrucción `assert` hasta que sepa que necesita reemplazarla por una corrección de código real. Supongamos que decide que el usuario pueda encontrarse con la excepción en una versión de lanzamiento de la aplicación. En ese caso, debe refactorizar el código para asegurarse de que la aplicación no produzca una excepción grave u otro error. Por lo tanto, para corregir este código, reemplace el código siguiente:

```csharp
if (existingUser == false)
{
    User user = new User();
```

con este código:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Así, cumplirá los requisitos de código y se asegurará de que no se agregue a los datos un registro con un valor `firstname` o `lastname` de `null`.

En este ejemplo, se han agregado las dos instrucciones `assert` dentro de un bucle. Normalmente, cuando se usa `assert`, es mejor agregar instrucciones `assert` en el punto de entrada (al comienzo) de una función o método. Actualmente está examinando el método `UpdateRecords` en la aplicación de ejemplo. En este método, sabe que tendrá problemas si alguno de los argumentos del método es `null`, por lo que debe comprobarlos con una instrucción `assert` en el punto de entrada de la función.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

En el caso de las instrucciones anteriores, su intención es cargar los datos existentes (`db`) y recuperar nuevos datos (`users`) antes de actualizar nada.

Puede usar `assert` con cualquier tipo de expresión que se resuelva como `true` o `false`. Por lo tanto, a modo de ejemplo, puede agregar una instrucción `assert` como esta.

```csharp
Debug.Assert(users[0].points > 0);
```

El código anterior resulta útil si quiere especificar la siguiente intención: se requiere un nuevo valor de punto mayor que cero (0) para actualizar el registro del usuario.

## <a name="inspect-your-code-in-the-debugger"></a>Inspección del código en el depurador

Bien. Ahora que ha corregido todo lo crítico que estaba mal en la aplicación de ejemplo, puede pasar a otras cosas importantes.

Se le mostró el asistente de excepciones del depurador, pero el depurador es una herramienta mucho más eficaz que también le permite hacer otras cosas, como recorrer paso a paso el código e inspeccionar sus variables. Estas funcionalidades más eficaces son útiles en muchos escenarios, especialmente los siguientes:

* Intenta aislar un error en tiempo de ejecución en el código, pero no puede hacerlo con los métodos y herramientas descritos anteriormente.

* Quiere validar el código, es decir, verlo mientras se ejecuta para asegurarse de que se comporte de la manera esperada y de que haga lo previsto.

    Es instructivo ver el código mientras se ejecuta. De esta forma, puede obtener más información sobre el código y, frecuentemente, identificar errores antes de que se manifiesten síntomas evidentes.

Para obtener información sobre el uso de las características esenciales del depurador, vea [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Los errores de otro tipo incluyen el código ineficaz que provoca que la aplicación se ejecute más lentamente o que consuma demasiada memoria. Generalmente, la optimización del rendimiento es algo que puede hacer más adelante en el desarrollo de la aplicación. Sin embargo, puede experimentar problemas de rendimiento al principio (por ejemplo, puede ver que alguna parte de la aplicación se ejecuta lentamente) y es posible que tenga que probar la aplicación con las herramientas de generación de perfiles en un momento anterior. Para obtener más información sobre herramientas de generación de perfiles como Uso de CPU y Analizador de memoria, vea [un primer vistazo a las herramientas de generación de perfiles](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Pasos siguientes

En este artículo ha aprendido a evitar y corregir muchos errores comunes en el código y cuándo usar el depurador. A continuación, obtenga más información sobre cómo usar el depurador de Visual Studio para corregir errores.

> [!div class="nextstepaction"]
> [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md)
