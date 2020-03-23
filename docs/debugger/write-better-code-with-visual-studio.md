---
title: Herramientas y técnicas de depuración
description: Escribir mejor código con menos errores mediante Visual Studio para corregir excepciones, corregir errores y mejorar el código
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301024"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Técnicas y herramientas de depuración para ayudarle a escribir mejor código

Corregir errores y errores en el código puede ser una tarea que consume mucho tiempo (y a veces frustrante). Se necesita tiempo para aprender a depurar eficazmente, pero un IDE eficaz como Visual Studio puede hacer su trabajo mucho más fácil. Un IDE puede ayudarle a corregir errores y depurar el código más rápidamente, y no solo eso, sino que también puede ayudarle a escribir mejor código con menos errores. Nuestro objetivo en este artículo es darle una visión holística del proceso de "corrección de errores", para que sepa cuándo usar el analizador de código, cuándo usar el depurador, cómo corregir excepciones y cómo codificar para la intención. Si ya sabe que necesita usar el depurador, consulte [Primero, examine el depurador.](../debugger/debugger-feature-tour.md)

En este artículo, hablamos sobre cómo aprovechar el IDE para que las sesiones de codificación sean más productivas. Tocamos varias tareas, tales como:

* Prepare el código para la depuración aprovechando el analizador de código del IDE

* Cómo corregir excepciones (errores en tiempo de ejecución)

* Cómo minimizar los errores mediante la codificación de la intención (mediante la aserción)

* Cuándo utilizar el depurador

Para demostrar estas tareas, mostramos algunos de los tipos más comunes de errores y errores que encontrará al intentar depurar sus aplicaciones. Aunque el código de ejemplo es de C, la información conceptual es generalmente aplicable a C++, Visual Basic, JavaScript y otros lenguajes admitidos por Visual Studio (excepto donde se indique). Las capturas de pantalla son de código C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Crear una aplicación de ejemplo con algunos errores y errores en ella

El código siguiente tiene algunos errores que puede corregir mediante el IDE de Visual Studio. La aplicación aquí es una aplicación sencilla que simula la obtención de datos JSON de alguna operación, la deserialización de los datos a un objeto y la actualización de una lista simple con los nuevos datos.

Para crear la aplicación:

1. Debe tener Visual Studio instalado y el desarrollo entre plataformas de **.NET Core** o la carga de trabajo de desarrollo de escritorio de **.NET** instalado, dependiendo del tipo de aplicación que desee crear.

    Si aún no ha instalado Visual Studio, vaya a la página de [descargas](https://visualstudio.microsoft.com/downloads/) de Visual Studio para instalarlo de forma gratuita.

    Si necesita instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en **Herramientas** > **obtener herramientas y características**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo de desarrollo entre plataformas **Modify**o de desarrollo de escritorio de **.NET.** **.NET desktop development**

1. Abra Visual Studio.

    ::: moniker range=">=vs-2019"
    En la ventana de inicio, elija **Create a new project**. Escriba **console** en el cuadro de búsqueda y, a continuación, elija **Console App (.NET Core)** o **Console App (.NET Framework).** Elija **Siguiente**. Escriba un nombre de proyecto como **Console_Parse_JSON** y haga clic en **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **nuevo** > **proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto** , en **Visual C,** elija **Aplicación**de consola y, a continuación, en el panel central, elija Aplicación de consola **(.NET Core)** o Aplicación de **consola (.NET Framework).** Escriba un nombre como **Console_Parse_JSON** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto Aplicación de consola **(.NET Core)** o Aplicación de **consola (.NET Framework),** vaya a **Herramientas** > obtener**herramientas y características,** que abre el instalador de Visual Studio. Elija el desarrollo entre plataformas de **.NET Core** o la carga de trabajo de desarrollo de escritorio de **.NET** y, a continuación, elija **Modify**.

    Visual Studio crea el proyecto de consola, con lo que aparece el Explorador de soluciones (en el panel derecho).

1. Reemplace el código predeterminado del archivo *de Program.cs* del proyecto por el código de ejemplo siguiente.

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

## <a name="find-the-red-and-green-squiggles"></a>¡Encuentra los ondulados rojos y verdes!

Antes de intentar iniciar la aplicación de ejemplo y ejecutar el depurador, compruebe el código en el editor de código para las ondulaciones rojas y verdes. Estos representan errores y advertencias identificados por el analizador de código del IDE. Las ondulaciones rojas son errores en tiempo de compilación, que debe corregir antes de poder ejecutar el código. Los ondulados verdes son advertencias. Aunque a menudo puede ejecutar la aplicación sin corregir las advertencias, pueden ser una fuente de errores y a menudo se ahorra tiempo y problemas al investigarlos. Estas advertencias y errores también aparecen en la ventana **Lista** de errores, si prefiere una vista de lista.

En la aplicación de ejemplo, verá varias ondulaciones rojas que necesita corregir y una verde que verá. Aquí está el primer error.

![Error que se muestra como un ondulado rojo](../debugger/media/write-better-code-red-squiggle.png)

Para corregir este error, verá otra característica del IDE, representada por el icono de bombilla.

## <a name="check-the-light-bulb"></a>¡Compruebe la bombilla!

El primer ondulado rojo representa un error en tiempo de compilación. Pase el cursor sobre ```The name `Encoding` does not exist in the current context```él y verá el mensaje .

Tenga en cuenta que este error muestra un icono de bombilla en la parte inferior izquierda. Junto con el ![icono](../ide/media/screwdriver-icon.png)del destornillador del destornillador, el](../ide/media/light-bulb-icon.png) icono de la ![bombilla del icono de la bombilla de la bombilla representa las acciones rápidas que pueden ayudarle a fijar o refactorizar el código en línea. La bombilla representa problemas que *debe* solucionar. El destornillador es para problemas que puede elegir solucionar. Utilice la primera corrección sugerida para resolver este error haciendo clic en **System.Text** a la izquierda.

![Utilice la bombilla para arreglar el código](../debugger/media/write-better-code-missing-include.png)

Al hacer clic en este elemento, Visual Studio agrega la `using System.Text` instrucción en la parte superior del archivo *Program.cs* y el ondulado rojo desaparece. (Cuando no esté seguro de lo que hará una corrección sugerida, elija el vínculo **Vista previa de cambios** a la derecha antes de aplicar la corrección.)

El error anterior es un error común que `using` normalmente se corrige agregando una nueva instrucción al código. Hay varios errores comunes y similares ```The type or namespace `Name` cannot be found.``` a este, como Estos tipos de errores pueden indicar una referencia de ensamblado que falta (haga clic con el botón derecho en el proyecto, elija **Agregar** > **referencia**), un nombre mal escrito o una biblioteca que falte que necesite agregar (para C, haga clic con el botón derecho en el proyecto y elija **Administrar paquetes NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Corregir los errores y advertencias restantes

Hay algunos squiggles más para ver en este código. Aquí, verá un error de conversión de tipos común. Al pasar el cursor sobre el squiggle, verá que el código está intentando convertir una cadena en un int, que no se admite a menos que agregue código explícito para realizar la conversión.

![Error de conversión de tipos](../debugger/media/write-better-code-conversion-error.png)

Debido a que el analizador de código no puede adivinar su intención, no hay bombillas para ayudarle esta vez. Para corregir este error, debe conocer la intención del código. En este ejemplo, no es demasiado `points` difícil ver que debe ser un valor numérico `points` `totalpoints`(entero), ya que está intentando agregar a .

Para corregir este error, cambie el `points` miembro de la `User` clase de esto:

```csharp
[DataMember]
internal string points;
```

a esto:

```csharp
[DataMember]
internal int points;
```

Las líneas onduladas rojas en el editor de código desaparecen.

A continuación, coloque el cursor sobre el `points` ondulado verde en la declaración del miembro de datos. El analizador de código indica que a la variable nunca se le asigna un valor.

![Mensaje de advertencia para la variable sin asignar](../debugger/media/write-better-code-warning-message.png)

Normalmente, esto representa un problema que debe corregirse. Sin embargo, en la aplicación de ejemplo, de hecho está almacenando datos en la `points` variable durante el proceso de deserialización y, a continuación, agregando ese valor al `totalpoints` miembro de datos. En este ejemplo, conoce la intención del código y puede omitir la advertencia de forma segura. Sin embargo, si desea eliminar la advertencia, puede reemplazar el código siguiente:

```csharp
item.totalpoints = users[i].points;
```

por este:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

El squiggle verde desaparece.

## <a name="fix-an-exception"></a>Corregir una excepción

Cuando haya arreglado todas las ondulaciones rojas y resuelto (o al menos investigado) todos los ondulados verdes, estará listo para iniciar el depurador y ejecutar la aplicación.

Presione **F5** (**Depurar > Iniciar depuración**) o el botón Iniciar **depuración** ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas Depurar.

En este punto, la aplicación `SerializationException` de ejemplo produce una excepción (un error en tiempo de ejecución). Es decir, la aplicación se ahoga en los datos que está intentando serializar. Dado que ha iniciado la aplicación en modo de depuración (depurador adjunto), la aplicación auxiliar de excepciones del depurador le lleva directamente al código que produjo la excepción y le proporciona un mensaje de error útil.

![Se produce una SerializationException](../debugger/media/write-better-code-serialization-exception.png)

El mensaje de error le `4o` indica que el valor no se puede analizar como un entero. Por lo tanto, en este ejemplo, `4o` usted `40`sabe que los datos son malos: debe ser . Sin embargo, si no tiene el control de los datos en un escenario real (digamos que los está obteniendo de un servicio web), ¿qué hace al respecto? ¿Cómo lo arreglaría?

Cuando usted golpea una excepción, usted necesita hacer (y responder) un par de preguntas:

* ¿Es esta excepción sólo un error que puede corregir? O bien,

* ¿Es esta excepción algo que los usuarios pueden encontrar?

Si es el primero, arregla el error. (En la aplicación de ejemplo, eso significa corregir los datos incorrectos.) Si es este último, es posible que deba controlar `try/catch` la excepción en el código mediante un bloque (examinamos otras estrategias posibles en la siguiente sección). En la aplicación de ejemplo, reemplace el código siguiente:

```csharp
users = ser.ReadObject(ms) as User[];
```

por este otro:

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

Un `try/catch` bloque tiene algún costo de rendimiento, por lo que solo querrá usarlos cuando realmente los necesite, es decir, donde (a) pueden producirse en la versión de lanzamiento de la aplicación y donde (b) la documentación del método indica que debe comprobar la excepción (suponiendo que la documentación está completa!). En muchos casos, puede controlar una excepción de forma adecuada y el usuario nunca tendrá que saberlo.

Aquí hay un par de consejos importantes para el control de excepciones:

* Evite usar un bloque `catch (Exception) {}`catch vacío, como , que no tome las medidas adecuadas para exponer o controlar un error. Un bloque catch vacío o no informativo puede ocultar excepciones y puede hacer que el código sea más difícil de depurar en lugar de más fácil.

* Use `try/catch` el bloque alrededor de la función específica que produce la excepción (`ReadObject`, en la aplicación de ejemplo). Si lo usa alrededor de un fragmento de código más grande, termina ocultando la ubicación del error. Por ejemplo, no use `try/catch` el bloque alrededor de `ReadToObject`la llamada a la función primaria , que se muestra aquí, o no sabrá exactamente dónde se produjo la excepción.

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

* Para las funciones desconocidas que incluya en la aplicación, especialmente las que interactúan con datos externos (como una solicitud web), compruebe la documentación para ver qué excepciones es probable que produzca la función. Esto puede ser información crítica para el control de errores adecuado y para depurar la aplicación.

Para la aplicación de `SerializationException` ejemplo, corrija `4o` `40`el método en el `GetJsonData` cambio a .

## <a name="clarify-your-code-intent-by-using-assert"></a>Aclarar la intención del código mediante el uso de la aserción

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús** + **F5**). Esto reinicia la aplicación en menos pasos. Verá la siguiente salida en la ventana de la consola.

![Valor nulo en la salida](../debugger/media/write-better-code-using-assert-null-output.png)

Puede ver algo en esta salida que no está del todo bien. **nombre** y **apellido** para el tercer registro están en blanco!

Este es un buen momento para hablar sobre una práctica de `assert` codificación útil, a menudo infrautilizada, que es usar instrucciones en las funciones. Al agregar el código siguiente, se incluye `firstname` una `lastname` comprobación `null`en tiempo de ejecución para asegurarse de que y no son . Reemplace el código `UpdateRecords` siguiente en el método:

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

Al `assert` agregar instrucciones como esta a las funciones durante el proceso de desarrollo, puede ayudar a especificar la intención del código. En el ejemplo anterior, especificamos lo siguiente:

* Se requiere una cadena válida para el nombre
* Se requiere una cadena válida para el apellido

Al especificar la intención de esta manera, se aplican los requisitos. Este es un método simple y práctico que puede utilizar para exponer errores durante el desarrollo. (`assert` las instrucciones también se utilizan como elemento principal en las pruebas unitarias.)

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús** + **F5**).

> [!NOTE]
> El `assert` código solo está activo en una compilación de depuración.

Al reiniciar, el depurador se `assert` detiene en `users[i].firstname != null` la `false` instrucción, porque la expresión se evalúa en lugar de `true`.

![Assert se resuelve en falso](../debugger/media/write-better-code-using-assert.png)

El `assert` error le indica que hay un problema que necesita investigar. `assert`puede cubrir muchos escenarios en los que no se ve necesariamente una excepción. En este ejemplo, el usuario no verá `null` una excepción `firstname` y se agrega un valor como en la lista de registros. Esto puede causar los problemas más adelante (tal como usted ve en la salida de la consola) y pudo ser más difícil de depurar.

> [!NOTE]
> En escenarios donde se llama `null` a `NullReferenceException` un método en el valor, un resultados. Normalmente desea evitar `try/catch` el uso de un bloque para una excepción general, es decir, una excepción que no está vinculada a la función de biblioteca específica. Cualquier objeto puede `NullReferenceException`lanzar un archivo . Compruebe la documentación de la función de biblioteca si no está seguro.

Durante el proceso de depuración, es `assert` bueno mantener una instrucción determinada hasta que sepa que necesita reemplazarla con una corrección de código real. Supongamos que decide que el usuario puede encontrar la excepción en una versión de lanzamiento de la aplicación. En ese caso, debe refactorizar el código para asegurarse de que la aplicación no produce una excepción fatal o da lugar a algún otro error. Por lo tanto, para corregir este código, reemplace el siguiente código:

```csharp
if (existingUser == false)
{
    User user = new User();
```

por este otro:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Con este código, cumple los requisitos de código `firstname` y `lastname` se `null` asegura de que no se agrega un registro con un o valor de no se agrega a los datos.

En este ejemplo, agregamos las dos `assert` instrucciones dentro de un bucle. Normalmente, cuando `assert`se usa , `assert` es mejor agregar instrucciones en el punto de entrada (principio) de una función o método. Actualmente está mirando `UpdateRecords` el método en la aplicación de ejemplo. En este método, sabe que está en problemas si `null`cualquiera de los `assert` argumentos del método es , así que compruebe ambos con una instrucción en el punto de entrada de la función.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Para las instrucciones anteriores, la intención es`db`cargar datos existentes`users`( ) y recuperar nuevos datos ( ) antes de actualizar nada.

Puede utilizar `assert` con cualquier tipo de `true` expresión `false`que se resuelva en o . Así, por ejemplo, podría `assert` agregar una instrucción como esta.

```csharp
Debug.Assert(users[0].points > 0);
```

El código anterior es útil si desea especificar la siguiente intención: se requiere un nuevo valor de punto mayor que cero (0) para actualizar el registro del usuario.

## <a name="inspect-your-code-in-the-debugger"></a>Inspeccione el código en el depurador

OK, ahora que has arreglado todo lo crítico que está mal con la aplicación de ejemplo, ¡puedes pasar a otras cosas importantes!

Le mostramos la aplicación auxiliar de excepciones del depurador, pero el depurador es una herramienta mucho más eficaz que también le permite hacer otras cosas como recorrer el código e inspeccionar sus variables. Estas capacidades más potentes son útiles en muchos escenarios, especialmente los siguientes:

* Está intentando aislar un error en tiempo de ejecución en el código, pero no puede hacerlo mediante métodos y herramientas anteriormente discutidos.

* Desea validar el código, es decir, verlo mientras se ejecuta para asegurarse de que se comporta de la manera que espera y hacer lo que desea.

    Es instructivo ver el código mientras se ejecuta. Puede obtener más información sobre el código de esta manera y, a menudo, puede identificar errores antes de que manifiesten síntomas obvios.

Para obtener información sobre cómo usar las características esenciales del depurador, vea [Depuración para principiantes absolutos.](../debugger/debugging-absolute-beginners.md)

## <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Los errores de otro tipo incluyen código ineficiente que hace que la aplicación se ejecute lentamente o que use demasiada memoria. Por lo general, optimizar el rendimiento es algo que se hace más adelante en el desarrollo de aplicaciones. Sin embargo, puedes tener problemas de rendimiento antes de tiempo (por ejemplo, ves que alguna parte de la aplicación se está ejecutando lentamente) y es posible que debas probar la aplicación con las herramientas de generación de perfiles desde el principio. Para obtener más información acerca de las herramientas de generación de perfiles, como la herramienta Uso de CPU y el Analizador de memoria, consulte Primero, examine las herramientas de generación de [perfiles.](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido a evitar y corregir muchos errores comunes en el código y cuándo usar el depurador. A continuación, obtenga más información sobre el uso del depurador de Visual Studio para corregir errores.

> [!div class="nextstepaction"]
> [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md)
