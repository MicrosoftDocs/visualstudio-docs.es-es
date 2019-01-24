---
title: Solucione errores escribiendo mejor el código de C#
description: Aprender a escribir código mejor con menos errores
ms.custom:
- debug-experiment
- seodec18
ms.date: 11/20/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6be1f46c8a529eb7f2e7d21e34fb1a58458a3de
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967581"
---
# <a name="fix-bugs-by-writing-better-c-code-using-visual-studio"></a>Corregir errores al escribir mejor C# código con Visual Studio

Depuración de código puede llevar mucho tiempo y a veces frustrante--la tarea. Se necesita tiempo para obtener información sobre cómo depurar de forma eficaz, pero un eficaz IDE como Visual Studio puede hacer mucho más fácil su trabajo. Un IDE puede ayudarle a depurar el código más rápidamente y no sólo eso, sino también puede ayudarle a escribir código mejor con menos errores. Nuestro objetivo en este artículo es proporcionarle una visión holística del proceso de depuración, para que sepa cuándo se debe usar el analizador de código, al que se usará el depurador y cuándo usar otras herramientas.

En este artículo, hablamos sobre el aprovechamiento del IDE para aumentar la productividad de las sesiones de depuración. Nos toque en varias tareas, tales como:

* Preparar el código para la depuración mediante el aprovechamiento de analizador de código del IDE

* Cómo solucionar excepciones (errores de tiempo de ejecución)

* Cómo minimizar los errores mediante la codificación de intención

* Cuándo se debe usar el depurador

Para demostrar estas tareas, se muestran algunos de los tipos más comunes de errores y errores que nos encontramos al intentar depurar sus aplicaciones. Aunque el código de ejemplo es C#, la información conceptual es generalmente se aplica a C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indique). Las capturas de pantalla son de código C#.

## <a name="follow-along-using-the-sample-app"></a>Seguir utilizando la aplicación de ejemplo

Si lo prefiere, puede crear una aplicación de consola de .NET Framework o .NET Core que contiene los errores exactos y los errores que se describen aquí, y puede seguir el tutorial y realizar las correcciones usted mismo.

Para crear la aplicación, abra Visual Studio y elija **archivo > Nuevo proyecto**. En **Visual C#** , elija **Windows Desktop** o **.NET Core**y, a continuación, en el panel central, elija un **aplicación de consola**. Escriba un nombre como **Console_Parse_JSON** y haga clic en **Aceptar**. Visual Studio crea el proyecto. Pegar la [código de ejemplo](#sample-code) en el proyecto *Program.cs* archivo.

> [!NOTE]
> Si no ve la plantilla de proyecto **Aplicación de consola**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** o la carga de trabajo **Desarrollo multiplataforma de .NET Core**, y después elija **Modificar**.

## <a name="find-the-red-and-green-squiggles"></a>Encuentre el subrayado ondulado rojo y verde.

Antes de intentar iniciar la aplicación de ejemplo y ejecutar al depurador, compruebe el código en el editor de código para el subrayado ondulado rojo y verde. Estos representan errores y advertencias que se identifican mediante el analizador de código del IDE. El subrayado ondulado rojo es errores en tiempo de compilación, que se debe corregir antes de poder ejecutar el código. Los subrayados ondulados verdes son advertencias. Aunque a menudo puede ejecutar la aplicación sin solucionar las advertencias, pueden ser una fuente de errores y a menudo ahorra tiempo y problemas mediante la investigación de ellos. Estas advertencias y errores se muestran en el **lista de errores** ventana, si prefiere una vista de lista.

En la aplicación de ejemplo, verá varios un subrayado ondulado rojo que deba corregir y uno verde que se revisará. Este es el primer error.

![Error que se muestra como un subrayado ondulado de color rojo](../debugger/media/write-better-code-red-squiggle.png)

Para corregir este error, examinarán otra característica del IDE, representado por el icono de bombilla.

## <a name="check-the-light-bulb"></a>Compruebe la bombilla.

La primera línea en zigzag roja representa un error de tiempo de compilación. Mantenga el mouse sobre él y verá el mensaje ```The name `Encoding` does not exist in the current context```.

Tenga en cuenta que este error se muestra un icono de bombilla a la parte inferior izquierda. Además del icono destornillador ![icono destornillador](../ide/media/screwdriver-icon.png), el icono de bombilla ![icono de bombilla](../ide/media/light-bulb-icon.png) representa las acciones rápidas que puede ayudarle a corregir o refactorizar código alineado. Representa una bombilla problemas que usted *debe* corregir. El destornillador es para los problemas que desee corregir. Utilice la primera corrección sugerida para resolver este error, haga clic en **mediante System.Text** a la izquierda.

![Use la bombilla para corregir el código](../debugger/media/write-better-code-missing-include.png)

Al hacer clic en este artículo, Visual Studio agrega el `using System.Text` instrucción en la parte superior de la *Program.cs* archivo y el subrayado ondulado de color rojo desaparece. (Cuando no está seguro de lo que hará una sugerencia de corrección, elija el **vista previa de cambios** vínculo a la derecha antes de aplicar la corrección.)

El error anterior es común que normalmente se corrige agregando un nuevo `using` instrucción en el código. Existen varios errores comunes, de forma similares a este como ```The type or namespace `Name` cannot be found.``` estos tipos de errores pueden indicar una referencia de ensamblado que falta (haga clic en el proyecto, elija **agregar** > **referencia**), un nombre mal escrito o una biblioteca que faltan que deba agregar mediante NuGet (haga clic en el proyecto y elija **administrar paquetes de NuGet**).

## <a name="fix-the-errors-and-warnings"></a>Corrija los errores y advertencias

Hay unos subrayados ondulados más mirar en este código. En este caso, verá un error de conversión de tipo común. Al mantener el mouse sobre la línea ondulada, verá que el código intenta convertir una cadena en un entero, que no se admite a menos que agregue código explícito para efectuar la conversión.

![Error de conversión de tipo](../debugger/media/write-better-code-conversion-error.png)

Dado que el analizador de código no puede adivinar su intención, no hay ningún bombillas para ayudarle en este momento. Para corregir este error, deberá saber la intención del código. En este ejemplo, no es demasiado difícil ver que `points` debe ser un valor numérico (entero), ya que está intentando agregar `points` a `totalpoints`.

Para corregir este error, cambie el `points` miembro de la `User` clase a partir de esto:

```csharp
[DataMember]
internal string points;
```

a:

```csharp
[DataMember]
internal int points;
```

Las líneas onduladas rojas en el editor de código desaparecen.

A continuación, mantenga el mouse sobre el verde ondulado en la declaración de la `points` miembro de datos. El analizador de código indica a que la variable nunca se asigna un valor.

![Mensaje de advertencia para la variable no asignada](../debugger/media/write-better-code-warning-message.png)

Normalmente, esto representa un problema que debe solucionarse. Sin embargo, en la aplicación de ejemplo en realidad está almacenando datos en el `points` variable durante el proceso de deserialización y, a continuación, agrega el valor para el `totalpoints` miembro de datos. En este ejemplo, saber la intención del código y puede ignorar la advertencia. Sin embargo, si desea eliminar la advertencia, puede reemplazar el código siguiente:

```csharp
item.totalpoints = users[i].points;
```

por este:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

El subrayado ondulado de color verde desaparece.

## <a name="fix-an-exception"></a>Corregir una excepción

Cuando haya corregido todos los subrayados ondulados rojos y resuelve--o al menos investigar--todos el subrayado ondulado verde, está listo para iniciar al depurador y ejecutar la aplicación.

Presione **F5** (**Depurar > Iniciar depuración**) o el botón **Iniciar depuración** ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Start Debugging") en la barra de herramientas de depuración.

En este momento, la aplicación de ejemplo produce un `SerializationException` excepción (un error en tiempo de ejecución). Es decir, la aplicación hace que se retraiga en los datos que está intentando volver a serializar. Dado que inició la aplicación en modo de depuración (depurador adjunto), aplicación auxiliar de excepciones del depurador le lleva directamente al código que produjo la excepción y le ofrece un mensaje de error útiles.

![Se produce una excepción](../debugger/media/write-better-code-serialization-exception.png)

El mensaje de error indica que el valor `4o` no se puede analizar como un entero. Por lo tanto, en este ejemplo, sabrá que los datos están incorrectos: `4o` debe ser `40`. Sin embargo, si no está en el control de los datos en un escenario real (por ejemplo, se reciben de un servicio web), ¿qué hacer sobre ella? ¿Cómo lo arreglaría?

Cuando se produce una excepción, es preciso formular (y responder) un par de preguntas:

* ¿Es esta excepción simplemente un error que puede solucionar? O bien,

* ¿Es algo que los usuarios pueden producirse esta excepción?

Si es el primero, corrija el error. (En la aplicación de ejemplo, esto significa que corregir los datos incorrectos.) Si trata del último caso, es posible que deba controlar la excepción en el código utilizando un `try/catch` bloque (veremos otros posibles soluciones en la sección siguiente). En la aplicación de ejemplo, reemplace el código siguiente:

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

Un `try/catch` bloque tiene algún costo de rendimiento, por lo que solo desee usarlas cuando realmente los necesite, es decir, donde (a) se pueden producir en la versión de lanzamiento de la aplicación y dónde (b) la documentación para el método indica que debe comprobar si el excepción (suponiendo que la documentación completa!). En muchos casos, puede controlar una excepción de forma adecuada y el usuario nunca tendrá que tener conocimientos sobre él.

Existen un par de sugerencias importantes para el control de excepciones:

* Evite el uso de un bloque catch vacío, como `catch (Exception) {}`, que no toma las medidas adecuadas para exponer o controlar un error. Un bloque catch vacío o que no son informativos puede ocultar las excepciones y puede hacer que su código más difícil de depurar en el lugar más fácil.

* Use la `try/catch` bloque alrededor de la función específica que produce la excepción (`ReadObject`, en la aplicación de ejemplo). Si desea usarla en torno a un fragmento de código mayor, terminará la ocultación de la ubicación del error. Por ejemplo, no use la `try/catch` bloque alrededor de la llamada a la función primaria `ReadToObject`, se muestra a continuación, o no sabe exactamente dónde se produjo la excepción.

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

* Para obtener información sobre las funciones desconocidas que incluir en la aplicación, expecially aquellos interactuar con datos externos (por ejemplo, una solicitud web), consulte la documentación para ver qué excepciones la función es probable que se inicie. Esto puede ser información crítica para el control de errores adecuado y para depurar su aplicación.

Para la aplicación de ejemplo, corregir la `SerializationException` en el `GetJsonData` método cambiando `4o` a `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Aclarar la intención del código mediante el uso de assert

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas Depuración (**Ctrl** + **Mayús**  +  **F5**). Esto reinicia la aplicación en menos pasos. Consulte el siguiente resultado en la ventana de consola.

![Valor null en la salida](../debugger/media/write-better-code-using-assert-null-output.png)

Puede ver algo en este resultado no es correcto. **nombre** y **lastname** para el tercer registro están en blanco.

Se trata de un buen momento para hablar sobre una útil práctica de codificación, a menudo infrautilizada, que consiste en usar `assert` instrucciones en las funciones. Agregando el código siguiente, incluye una comprobación en tiempo de ejecución para asegurarse de que `firstname` y `lastname` no son `null`. Reemplace el código siguiente en el `UpdateRecords` método:

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

Agregando `assert` instrucciones así a las funciones durante el proceso de desarrollo, puede ayudar a especificar la intención del código. En el ejemplo anterior, se especifique lo siguiente:

* Se requiere para el nombre una cadena válida
* Se requiere para el último nombre de una cadena válida

Al especificar la intención de este modo, aplicar sus requisitos. Se trata de un método sencillo y útil que puede usar para la superficie de los errores durante el desarrollo. (`assert` instrucciones también se usan como el elemento principal de las pruebas unitarias.)

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas Depuración (**Ctrl** + **Mayús**  +  **F5**).

> [!NOTE]
> El `assert` código está activo solo en una compilación de depuración.

Cuando se reinicia, el depurador se detiene en el `assert` instrucción, porque la expresión `users[i].firstname != null` se evalúa como `false` en lugar de `true`.

![Se resuelve en false de Assert](../debugger/media/write-better-code-using-assert.png)

El `assert` error indica que hay un problema que necesita para investigar. `assert` puede cubrir muchos escenarios donde no aparecen necesariamente una excepción. En este ejemplo, el usuario no verá una excepción y un `null` valor se agrega como `firstname` en la lista de registros. Esto puede causar problemas más adelante (como ve en la salida de consola) y podría ser más difíciles de depurar.

> [!NOTE]
> En escenarios donde se llama a un método en el `null` valor, un `NullReferenceException` resultados. Normalmente deseará evitar usar un `try/catch` se bloquea durante una excepción general, es decir, una excepción que no está asociada a la función de biblioteca específico. Cualquier objeto puede producir un `NullReferenceException`. Consulte la documentación de la función de biblioteca si no está seguro.

Durante el proceso de depuración, es bueno tener un determinado `assert` instrucción hasta que se sabe que necesita para reemplazarla por una corrección de código real. Supongamos que decide que el usuario pueda encontrar la excepción en una versión de lanzamiento de la aplicación. En ese caso, debe refactorizar el código para asegurarse de que la aplicación no produzca una excepción grave o dar lugar a algún otro error. Por lo tanto, para corregir este código, reemplace el código siguiente:

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

Mediante el uso de este código, se satisfacen sus requisitos de código y asegúrese de que un registro con un `firstname` o `lastname` valor de `null` no se agrega a los datos.

En este ejemplo, hemos agregado dos `assert` instrucciones dentro de un bucle. Normalmente, cuando se usa `assert`, es mejor agregar `assert` instrucciones en el punto de entrada (inicio) de una función o método. Actualmente está mirando el `UpdateRecords` método en la aplicación de ejemplo. En este método, sabrá son problemas si cualquiera de los argumentos de método es `null`, por lo tanto, compruebe que ambos con un `assert` instrucción al punto de entrada de la función.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Para las instrucciones anteriores, su intención es que cargar los datos existentes (`db`) y recuperar los datos nuevos (`users`) antes de actualizar cualquier cosa.

Puede usar `assert` con cualquier tipo de expresión que se resuelve en `true` o `false`. Por lo tanto, por ejemplo, podría agregar un `assert` instrucción como esta.

```csharp
Debug.Assert(users[0].points > 0);
```

El código anterior es útil si desea especificar la intención siguiente: un nuevo valor de punto mayor que cero (0) es necesario para actualizar el registro del usuario.

## <a name="inspect-your-code-in-the-debugger"></a>Inspeccionar el código en el depurador

Bien, ahora que ha corregido todo lo crítica que es el problema con la aplicación de ejemplo, puede pasar a otras cosas importantes!

Le mostramos aplicación auxiliar de excepciones del depurador, pero el depurador es una herramienta mucho más eficaz que también le permite hacer otras cosas, como recorrer el código y examine sus variables. Estas capacidades más eficaces son útiles en muchos escenarios, especialmente en lo siguiente:

* Está intentando aislar un error en tiempo de ejecución en el código, pero no puede hacerlo mediante métodos y herramientas que se ha indicado anteriormente.

* Desee validar el código, es decir, verlo mientras se ejecuta para asegurarse de que se comporta de la manera esperada y hacer lo que desea para.

    Es instructivo para ver el código mientras se ejecuta. Puede obtener más información sobre el código de este modo y con frecuencia puede identificar los errores antes que cualquier síntoma obvia de manifiesto.

Para obtener información sobre cómo usar las características esenciales del depurador, vea [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Los errores de otro tipo incluyen código ineficaz que hace que la aplicación se ejecute lentamente o usar demasiada memoria. Por lo general, optimizar el rendimiento es algo que se hace más adelante en el desarrollo de aplicaciones. Sin embargo, puede encontrarse con problemas de rendimiento al principio (por ejemplo, verá que alguna parte de la aplicación se ejecuta demasiado lento), y es posible que deba probar la aplicación con las herramientas de generación de perfiles desde el principio. Para obtener más información sobre cómo generar perfiles de herramientas, como la herramienta de uso de CPU y el analizador de memoria, vea [primer vistazo a las herramientas de generación de perfiles](../profiling/profiling-feature-tour.md).

## <a name="sample-code"></a> Código de ejemplo

El código siguiente tiene algunos errores que pueden corregir mediante el IDE de Visual Studio. Aquí la aplicación es una aplicación sencilla que simula obtener los datos JSON de alguna operación, deserializar los datos a un objeto y actualizar una lista simple con los nuevos datos.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON_DotNetCore
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

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido cómo evitar y solucionar muchos errores comunes en el código y cuándo se debe utilizar al depurador. A continuación, obtenga más información sobre cómo usar al depurador de Visual Studio para corregir errores.

> [!div class="nextstepaction"]
> [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md)
