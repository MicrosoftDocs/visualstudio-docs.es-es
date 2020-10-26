---
title: Uso de .NET 4.x en Unity
description: Entienda cómo se usa .NET 4.x en Unity. Habilite el entorno de ejecución de scripting de .NET 4.x. Aproveche la compatibilidad de .NET. Revise las nuevas características de lenguaje y sintaxis.
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 06efbe9d346cbbe8b9e81d95be257742b659cf8f
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039851"
---
# <a name="using-net-4x-in-unity"></a>Uso de .NET 4.x en Unity

C# y .NET, las tecnologías subyacentes de scripting de Unity, han seguido recibiendo actualizaciones desde que Microsoft las publicó originalmente en 2002. Pero los desarrolladores de Unity no pueden tener en cuenta el flujo constante de las nuevas características que se agregan al lenguaje C# y .NET Framework. Eso es porque antes de Unity 2017.1, Unity ha estado usando un runtime de scripting equivalente a .NET 3.5, por lo que faltan años de actualizaciones.

Con el lanzamiento de Unity 2017.1, Unity introdujo una versión experimental de su runtime de scripting actualizado a una versión compatible de .NET 4.6 C# 6. En Unity 2018.1, el runtime equivalente a .NET 4.x ya no se considera experimental, mientras que el runtime equivalente a .NET 3.5 se considera ahora la versión heredada. Y con el lanzamiento de Unity 2018.3, se prevé que Unity ofrezca el runtime de scripting actualizado como la selección predeterminada y actualice incluso más allá de C# 7. Para más información y obtener las actualizaciones más recientes en esta guía, lea la [entrada de blog](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) de Unity o visite el [foro de versiones preliminares del scripting experimental](https://forum.unity.com/forums/experimental-scripting-previews.107/). Mientras tanto, consulte las secciones siguientes para saber más sobre las nuevas características que ya están disponibles con el runtime de scripting de .NET 4.x.

## <a name="prerequisites"></a>Requisitos previos

* [Unity 2017.1 o superior](https://unity3d.com/) (2018.2 recomendado)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Habilitar el runtime de scripting de .NET 4.x en Unity

Para habilitar el runtime de scripting de .NET 4.x, siga estos pasos:

1. Abra Configuración del reproductor en el Inspector de Unity. Para ello, seleccione **Editar > Configuración del proyecto > Reproductor** .

1. En el encabezado **Configuración** , haga clic en el menú desplegable **Scripting Runtime Version** (Versión de runtime de scripting) y seleccione **.NET 4 Equivalent** (Equivalente a .NET 4.x). Se le solicitará que reinicie Unity.

![Seleccionar el equivalente de .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Elegir entre los perfiles .NET 4.x y .NET Standard 2.0

Una vez que haya cambiado al runtime de scripting equivalente a .NET 4.x, puede especificar **Api Compatibility Level** (Nivel de compatibilidad de API) mediante el menú desplegable en Configuración del reproductor ( **Editar > Configuración del proyecto > Reproductor** ). Hay dos opciones:

* **.NET Standard 2.0** . Este perfil coincide con el [perfil de .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) publicado por .NET Foundation. Unity recomienda .NET Standard 2.0 para los nuevos proyectos. Es menor que .NET 4.x, lo que supone una ventaja para plataformas de tamaño limitado. Además, Unity se ha comprometido a admitir este perfil en todas las plataformas compatibles con Unity.

* **.NET 4.x** . Este perfil proporciona acceso a la API de .NET 4 más reciente. Incluye todo el código disponible en las bibliotecas de clases de .NET Framework y admite también los perfiles de .NET Standard 2.0. Si el proyecto necesita parte de la API que no está incluida en el perfil de .NET Standard 2.0, use el perfil de .NET 4.x. Pero tenga en cuenta que algunas partes de esta API no se admiten en todas las plataformas de Unity.

Encontrará más información sobre estas opciones en esta [entrada del blog](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/) de Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Agregar referencias de ensamblado al usar el nivel de compatibilidad de la API de .NET 4.x

Al usar la opción .NET Standard 2.0 en el menú desplegable **Api Compatibility Level** (Nivel de compatibilidad de API), se pueden usar todos los ensamblados en el perfil de API y hacer referencia a ellos. Pero cuando se usa el perfil de 4.x de .NET más grande, no se hace referencia de manera predeterminada a algunos de los ensamblados que Unity envía. Para usar estas API, debe agregar manualmente una referencia de ensamblado. Puede ver los ensamblados que Unity envía en el directorio **MonoBleedingEdge/lib/mono** de la instalación del editor de Unity:

![Directorio MonoBleedingEdge](media/vstu_monobleedingedge.png)

Por ejemplo, si está usando el perfil de .NET 4.x y quiere usar `HttpClient`, debe agregar una referencia de ensamblado para System.Net.Http.dll. Sin ella, el compilador se quejará de que falta una referencia de ensamblado:

![falta referencia de ensamblado](media/vstu_missing-reference.png)

Visual Studio vuelve a generar los archivos .csproj y .sln para proyectos de Unity cada vez que se abren. Como resultado, no se pueden agregar referencias de ensamblado directamente en Visual Studio porque se perderán al volver a abrir el proyecto. En su lugar, debe usarse un archivo de texto especial denominado **mcs.rsp** :

1. Cree un nuevo archivo de texto denominado **mcs.rsp** en el directorio raíz **Assets** del proyecto de Unity.

1. En la primera línea del archivo de texto vacío, escriba `-r:System.Net.Http.dll` y guarde el archivo. Puede reemplazar "System.Net.Http.dll" con cualquier ensamblado incluido al que pueda faltarle una referencia.

1. Reinicie el editor de Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Aprovechar la compatibilidad de .NET

Además de la nueva sintaxis de C# y las características de idioma, el runtime de scripting de .NET 4.x ofrece a los usuarios de Unity acceso a una gran biblioteca de paquetes de .NET que no son compatibles con el runtime de scripting de .NET 3.5 heredado.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Agregar paquetes de NuGet a un proyecto de Unity

[NuGet](https://www.nuget.org/) es el administrador de paquetes para .NET. NuGet está integrado en Visual Studio, pero los proyectos de Unity deben seguir un proceso especial para agregar paquetes de NuGet. Esto se debe a que cuando se abre un proyecto de Unity, se vuelven a generar sus archivos de proyecto de Visual Studio, con lo que se deshacen las configuraciones necesarias. Para agregar un paquete de NuGet al proyecto de Unity, haga esto:

1. Examine NuGet para encontrar un paquete compatible que quiera agregar (.NET Standard 2.0 o .NET 4.x). En este ejemplo se muestra la adición de [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), un conocido paquete para trabajar con JSON, a un proyecto de .NET Standard 2.0.

1. Haga clic en el botón **Descargar** :

    ![botón descargar](media/vstu_nuget-download.png)

1. Busque el archivo descargado y cambie la extensión de **.nupkg** a **.zip** .

1. En el archivo zip, vaya al directorio **lib/netstandard2.0** y copie el archivo **Newtonsoft.Json.dll** .

1. En la carpeta raíz **Assets** del proyecto de Unity, cree una carpeta nueva denominada **Plugins** . Plugins es un nombre de carpeta especial en Unity. Eche un vistazo a la [documentación de Unity](https://docs.unity3d.com/Manual/Plugins.html) para más información.

1. Pegue el archivo **Newtonsoft.Json.dll** en el directorio **Plugins** del proyecto de Unity.

1. Cree un archivo denominado **link.xml** en el directorio **Assets** del proyecto de Unity y agregue el siguiente código XML.  Esto garantizará que el proceso de extracción de código de bytes de Unity no elimine los datos necesarios al exportar a una plataforma IL2CPP.  Aunque este paso es específico para esta biblioteca, es posible que experimente problemas con otras bibliotecas que usen Reflexión de manera similar.  Para más información,vea los [documentos de Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) en este tema.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Ahora que todo está donde le corresponde, ya puede usar el paquete Json.NET.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Esto es un ejemplo sencillo de cómo usar una biblioteca que no tiene ninguna dependencia. Cuando los paquetes de NuGet dependen de otros paquetes de NuGet, tendrá que descargar estas dependencias manualmente y agregarlas al proyecto de la misma manera.

## <a name="new-syntax-and-language-features"></a>Nuevas características de idioma y sintaxis

Al usar el runtime de scripting actualizado, los desarrolladores de Unity tienen acceso a C# 6 y un sinfín de nuevas características de idioma y sintaxis.

### <a name="auto-property-initializers"></a>Inicializadores de propiedades automáticas

En el runtime de scripting de .NET 3.5 de Unity, la sintaxis de propiedad automática facilita la tarea de definir rápidamente las propiedades sin inicializar, pero la inicialización tiene que producirse en cualquier otro lugar en el script. Ahora con el runtime de .NET 4.x, es posible inicializar propiedades automáticas en la misma línea:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolación de cadenas

Con el runtime de .NET 3.5 anterior, para la concatenación de cadenas se necesitaba una sintaxis extraña. Ahora con el runtime de .NET 4.x, la característica [ de `$`interpolación de cadenas](/dotnet/csharp/language-reference/tokens/interpolated) permite insertar expresiones en las cadenas en una sintaxis más legible y directa:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Miembros con forma de expresión

Con la nueva sintaxis de C# disponible en el runtime de .NET 4.x, las [expresiones lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) pueden reemplazar el cuerpo de las funciones para que sean más concisas:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

También se pueden usar miembros con cuerpo de expresión en propiedades de solo lectura:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Modelo asincrónico basado en tareas (TAP)

[Programación asincrónica](/dotnet/csharp/async) permite que las operaciones que tardan mucho en completarse se lleven a cabo sin provocar que la aplicación deje de responder. Esta función también permite que el código espere a que finalicen las operaciones que tardan mucho antes de seguir con el código que depende de los resultados de estas operaciones. Por ejemplo, puede esperar a que se cargue un archivo o a que se complete una operación de red.

En Unity, la programación asincrónica suele completarse con [corrutinas](https://docs.unity3d.com/Manual/Coroutines.html). Pero desde C# 5, el método preferido de la programación asincrónica en el desarrollo de .NET ha sido el [modelo asincrónico basado en tareas (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) usando las palabras clave `async` y `await` con [ System.Threading.Task](/dotnet/api/system.threading.tasks.task). En resumen, en una función `async` puede usar `await` para esperar a que finalice una tarea sin impedir que el resto de la aplicación se actualice:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP es un tema complejo que presenta matices específicos de Unity que los desarrolladores deben tener en cuenta. Como resultado, TAP no es una sustitución universal para corrutinas en Unity, sino que se trata de otra herramienta que se puede aprovechar. La descripción de esta característica va más allá del ámbito de este artículo, pero aquí ofrecemos algunas prácticas recomendadas y consejos generales.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Referencia de introducción a TAP con Unity

Estas sugerencias pueden ayudarle a empezar a trabajar con TAP en Unity:

* Las funciones asincrónicas destinadas a ser esperadas deben tener el tipo de valor devuelto [`Task`](/dotnet/api/system.threading.tasks.task) o [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1).
* Las funciones asincrónicas que devuelven una tarea deben tener el sufijo **"Async"** anexado a sus nombres. El sufijo "Async" le ayuda a indicar que siempre se debe esperar una función.
* Use solo el tipo de valor devuelto `async void` para las funciones que activan funciones asincrónicas desde el código sincrónico tradicional. Estas funciones no pueden ser esperadas y no deberían tener el sufijo "Async" en sus nombres.
* Unity usa UnitySynchronizationContext para asegurarse de que se ejecutarán las funciones asincrónicas en el subproceso principal de forma predeterminada. No se puede acceder a la API de Unity fuera del subproceso principal.
* Es posible ejecutar tareas en subprocesos en segundo plano con métodos como [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) y [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait). Esta técnica es útil para la descarga de operaciones costosas desde el subproceso principal para mejorar el rendimiento. Pero el uso de subprocesos en segundo plano puede provocar problemas que son difíciles de depurar, como las [condiciones de carrera](https://wikipedia.org/wiki/Race_condition).
* No se puede acceder a la API de Unity fuera del subproceso principal.
* Las tareas que usan subprocesos no se admiten en las compilaciones WebGL de Unity.

#### <a name="differences-between-coroutines-and-tap"></a>Diferencias entre corrutinas y TAP

Hay algunas diferencias importantes entre las corrutinas y TAP / async-await:

* Las corrutinas no pueden devolver valores, pero `Task<TResult>` sí que puede.
* No puede poner `yield` en una instrucción try-catch, ya que dificultaría el control de errores con corrutinas. Pero try-catch sí funciona con TAP.
* La característica de corrutina de Unity no está disponible en las clases que no derivan de MonoBehaviour. TAP es excelente para la programación asincrónica en esas clases.
* En este momento, Unity no sugiere que TAP sea el sustituto principal de corrutinas. La creación de perfiles es la única manera de conocer los resultados específicos de un enfoque con respecto a los de un proyecto determinado.

> [!NOTE]
> A partir de Unity 2018.2, no se admite por completo la depuración de métodos asincrónicos con puntos de interrupción, pero [se espera disponer de esta función en Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>operador nameof

El operador `nameof` obtiene el nombre de cadena de una variable, tipo o miembro. Algunos casos en los que `nameof` resulta útil es en los registros de errores y al obtener el nombre de cadena de una enumeración:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Atributos de información del llamador

Los [atributos de información del llamador](/dotnet/csharp/programming-guide/concepts/caller-information) proporcionan información sobre el llamador de un método. Debe proporcionar un valor predeterminado para cada parámetro que quiera usar con un atributo de información del llamador:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Uso de versión estática

[Uso de versión estática](/dotnet/csharp/language-reference/keywords/using-static) permite usar funciones estáticas sin necesidad de escribir su nombre de clase. Con el uso de versión estática, puede ahorrar espacio y tiempo si necesita usar varias funciones estáticas de la misma clase:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Consideraciones sobre IL2CPP

Al exportar su juego a plataformas como iOS, Unity usará su motor IL2CPP para "transpilar" IL en código de C++, que luego se compilará usando el compilador nativo de la plataforma de destino. En este caso, hay varias características de .NET que no son compatibles, como partes de Reflexión y el uso de la palabra clave `dynamic`. Aunque puede controlar el uso de estas características en su propio código, es posible que tenga problemas al usar archivos DLL y SDK de terceros que no se escribieron pensando en Unity e IL2CPP. Para más información sobre este tema, vea los documentos sobre [restricciones de scripting](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) en el sitio de Unity.

Además, como se mencionó en el ejemplo anterior de Json.NET, Unity intentará eliminar código no utilizado durante el proceso de exportación de IL2CPP.  Aunque normalmente no es un problema, con las bibliotecas que usan Reflexión, puede que se eliminen accidentalmente las propiedades o los métodos que se llamarán en tiempo de ejecución y que no se pueden determinar en tiempo de exportación.  Para corregir estos problemas, agregue un archivo **link.xml** al proyecto que contiene una lista de ensamblados y espacios de nombres para que no se ejecute el proceso de extracción en ellos.  Para más información, vea los [documentos de Unity sobre la eliminación de código de bytes](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Proyecto de Unity de .NET 4.x de ejemplo

La muestra contiene ejemplos de varias características de .NET 4.x. Puede descargar el proyecto o ver el código fuente en [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Recursos adicionales

* [Unity Blog - Scripting Runtime Improvements in Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) (Blog de Unity: Mejoras del runtime de scripting en Unity 2018.2)
* [Historia de C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Novedades de C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronous programming in Unity, Using Coroutine and TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us) (Programación asincrónica en Unity usando corrutinas y TAP)
* [Async-Await Instead of Coroutines in Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/) (Async-Await en lugar de corrutinas en Unity 2017)
* [Unity Forum - Experimental Scripting Previews](https://forum.unity.com/forums/experimental-scripting-previews.107/) (Foro de Unity: Versiones preliminares del scripting experimental)