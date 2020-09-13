---
title: Información general | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f986d6727433dc01732232754b2d65d0d7c4ef8f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038288"
---
# <a name="overview-of-microsoft-intellitest"></a>Información general de Microsoft IntelliTest

IntelliTest le permite detectar errores pronto, y reduce los costos de mantenimiento de pruebas. Con un enfoque de pruebas transparente y automatizado, IntelliTest puede generar un conjunto candidato de pruebas para su código de .NET. La generación del conjunto de pruebas puede guiarse además mediante las *propiedades de corrección* que especifique. IntelliTest evolucionará incluso el conjunto de pruebas automáticamente a medida que el código sometido a prueba evolucione.

**Pruebas de caracterización** IntelliTest le permite determinar el comportamiento del código en términos de un conjunto de pruebas unitarias tradicionales.
Dicho conjunto de pruebas puede usarse como un conjunto de regresión que forma la base para tratar la complejidad asociada con la refactorización de código desconocido o heredado.

**Generación de entradas de prueba guiada** IntelliTest usa un análisis de código abierto y un enfoque de solución de restricciones para generar automáticamente valores de entrada de pruebas precisos; normalmente sin necesidad de la intervención del usuario. Para los tipos de objeto complejos, genera fábricas automáticamente. Puede guiar la generación de entradas de prueba ampliando y configurando las fábricas para que se adapten a sus requisitos. Las propiedades de corrección que se especifican como aserciones en el código también se usarán automáticamente para guiar más la generación de entradas de prueba.

**Integración en el IDE** IntelliTest está totalmente integrado en el IDE de Visual Studio. Toda la información recopilada durante la generación del conjunto de pruebas (como las entradas generadas automáticamente, el resultado del código, los casos de pruebas generados y su estado de superación o error) aparece en el IDE de Visual Studio. Puede iterar fácilmente entre corregir su código y volver a ejecutar IntelliTest, sin salir del IDE de Visual Studio.
Las pruebas pueden guardarse en la solución como un proyecto de prueba unitaria, y se detectarán automáticamente después mediante el Explorador de pruebas de Visual Studio.

**Complementar las prácticas de pruebas existentes** Use IntelliTest para complementar cualquier práctica de prueba existente que ya siga.

Si quiere probar:

* Algoritmos en datos primitivos o matrices de datos primitivos:
  * escriba [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing)
* Algoritmos en datos complejos, como el compilador:
  * permita que IntelliTest genere primero una representación abstracta de los datos y, después, la introduzca en el algoritmo
  * permita que IntelliTest cree instancias mediante la [creación de objetos personalizados](input-generation.md#objects) e invariantes de datos y, después, invoque el algoritmo
* Contenedores de datos:
  * escriba [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing)
  * permita que IntelliTest cree instancias mediante la [creación de objetos personalizados](input-generation.md#objects) e invariantes de datos y, después, invoque un método del contenedor y vuelva a comprobar después los elementos invariantes
  * escriba [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing) que llaman a diferentes métodos de la implementación, dependiendo de los valores de parámetro
* Una base de código existente:
  * use el Asistente de IntelliTest para Visual Studio para comenzar a generar un conjunto de [pruebas unitarias parametrizadas (PUT)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Hello World de IntelliTest

IntelliTest detecta entradas relevantes al programa que se prueba, lo que significa que puede usarlo para generar la famosa cadena **Hello World** (Hola a todos) . Presupone que ha creado un proyecto de prueba basado en MSTest de C# y que ha agregado una referencia a **Microsoft.Pex.Framework**. Si está usando un marco de prueba diferente, cree una biblioteca de clases de C# y vea la documentación del marco de prueba para obtener información sobre cómo configurar el proyecto.

En el ejemplo siguiente se crean dos restricciones en el parámetro denominado **value**, de manera que IntelliTest generará la cadena requerida:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Una vez que se haya compilado y ejecutado, IntelliTest genera un conjunto de pruebas de la manera siguiente:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> Para problemas de compilación, pruebe a reemplazar las referencias de Microsoft.VisualStudio.TestPlatform.TestFramework y Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions por una referencia a Microsoft.VisualStudio.QualityTools.UnitTestFramework.

Lea [Generar pruebas unitarias con IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) para saber dónde se guardan las pruebas generadas. El código de prueba generado debe incluir una prueba como la siguiente:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Es así de fácil.

Recursos adicionales:
  * Vea el [vídeo de Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest).
  * Lea esta [información general de MSDN Magazine](/archive/msdn-magazine/2015/february/visual-studio-2015-build-better-software-with-smart-unit-tests).

## <a name="important-attributes"></a>Atributos importantes

* [PexClass](attribute-glossary.md#pexclass) marca un tipo que contiene **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marca **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marca un parámetro que no es NULL

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) enlaza un proyecto de prueba a un proyecto
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) especifica un ensamblado que se va a instrumentar

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> clases del asistente estáticas importantes

* [PexAssume](static-helper-classes.md#pexassume) evalúa hipótesis (filtrado de entradas)
* [PexAssert](static-helper-classes.md#pexassert) evalúa aserciones
* [PexChoose](static-helper-classes.md#pexchoose) genera opciones nuevas (entradas adicionales)
* [PexObserve](static-helper-classes.md#pexobserve) registra valores en vivo para las pruebas generadas

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Limitaciones

En esta sección se describen las limitaciones de IntelliTest:

* [Indeterminismo](#nondeterminism)
* [Simultaneidad](#concurrency)
* [Código .NET nativo](#native-code)
* [Plataforma](#platform)
* [Idioma](#language)
* [Razonamiento simbólico](#symbolic-reasoning)
* [Seguimientos de la pila](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Indeterminismo

IntelliTest presupone que el programa analizado es determinista. Si no lo es, IntelliTest lo recorrerá hasta que alcance un límite de exploración.

IntelliTest considera que un programa no es determinista si se basa en entradas que IntelliTest no puede controlar.

IntelliTest controla entradas que se proporcionan para las [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing) y se obtienen de [PexChoose](static-helper-classes.md#pexchoose).
En ese sentido, los resultados de las llamadas a código no instrumentado o no administrado también se consideran como "entradas" en el programa instrumentado, pero IntelliTest no puede controlarlas. Si el flujo de control del programa depende de los valores específicos que provienen de estos orígenes externos, IntelliTest no puede "guiar" al programa hacia las áreas que no se han cubierto anteriormente.

Además, el programa se considera indeterminista si los valores de los orígenes externos cambian al volver a ejecutar el programa. En dichos casos, IntelliTest pierde el control de la ejecución del programa y su búsqueda pasa a ser ineficaz.

A veces no es evidente cuando esto sucede. Considere los siguientes ejemplos:

* El resultado del método **GetHashCode()** se proporciona mediante código no administrado y no es predecible.
* La clase **System.Random** usa la hora del sistema actual para proporcionar valores aleatorios reales.
* La clase **System.DateTime** proporciona la hora actual, que no está bajo el control de IntelliTest.

### <a name="concurrency"></a>simultaneidad

IntelliTest no controla los programas multiproceso.

### <a name="native-code"></a>Código nativo

IntelliTest no entiende el código nativo, como las instrucciones x86 que se llaman mediante **P/Invoke**. No sabe cómo traducir dichas llamadas en restricciones que se pueden pasar al [solucionador de restricciones](input-generation.md#constraint-solver).
Incluso para el código .NET, puede analizar solo código que instrumenta. IntelliTest no puede instrumentar determinadas partes de **mscorlib**, incluida la biblioteca de reflexión. **DynamicMethod** no se puede instrumentar.

La solución alternativa que se sugiere es tener un modo de prueba donde dichos métodos se encuentren en tipos de un ensamblado dinámico. En cambio, incluso si algunos métodos no están instrumentados, IntelliTest intentará cubrir el código instrumentado todo lo posible.

### <a name="platform"></a>Plataforma

IntelliTest solo se admite en .NETframework de 32 bits basado en X86.

### <a name="language"></a>Lenguaje

En principio, IntelliTest puede analizar los programas de .NET arbitrarios, escritos en cualquier lenguaje de .NET. En cambio, en Visual Studio solo admite C#.

### <a name="symbolic-reasoning"></a>Razonamiento simbólico

IntelliTest usa un [solucionador de restricciones](input-generation.md#constraint-solver) automático para determinar los valores que son relevantes para la prueba y el programa sometido a prueba. En cambio, las capacidades del solucionador de restricciones están, y siempre estarán, limitadas.

### <a name="incorrect-stack-traces"></a>Seguimientos de pila incorrectos

Como IntelliTest detecta y "vuelve a generar" excepciones en cada método instrumentado, los números de línea en los seguimientos de la pila no serán correctos. Esta es una limitación en el diseño de la instrucción "Rethrow".

## <a name="further-reading"></a>Información adicional

* [Entrada de blog de introducción](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generar pruebas unitarias para el código con IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)