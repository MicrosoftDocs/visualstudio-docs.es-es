---
title: Generación de pruebas | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
description: Obtenga información sobre cómo IntelliTest genera casos de prueba a partir de los métodos de la implementación y, después, genera entradas para los métodos y comprueba las aserciones en los datos.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a2ccb54995107bbd22e961f14ff3755b4a6f543a
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668084"
---
# <a name="test-generation"></a>Generación de pruebas

En las pruebas unitarias tradicionales, una prueba consta de varios elementos:

* Una [secuencia de llamadas a métodos](test-generation.md#test-generators).
* Los argumentos con los que se llaman a los métodos; los argumentos son las [entradas de prueba](input-generation.md).
* La validación del comportamiento previsto de la aplicación probada indicando un conjunto de [aserciones](#assumptions-and-assertions).

A continuación se muestra una estructura de prueba de ejemplo:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

A menudo, IntelliTest puede determinar automáticamente valores de argumento relevantes para [pruebas unitarias parametrizadas](#parameterized-unit-testing) más generales, que proporcionan la secuencia de llamadas al método y aserciones.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generadores de pruebas

IntelliTest genera casos de prueba seleccionando una secuencia de métodos de la implementación sometida a prueba que se va a ejecutar y, después, generando entradas para los métodos mientras se comprueban las aserciones en los datos derivados.

Una [prueba unitaria parametrizada](#parameterized-unit-testing) indica directamente en su cuerpo una secuencia de llamadas al método.

Cuando IntelliTest necesita crear objetos, llama a los constructores y los métodos de fábrica se agregarán automáticamente a la secuencia según sea necesario.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Pruebas unitarias parametrizadas

Las *Pruebas unitarias parametrizadas* (PUT) son pruebas que toman parámetros. A diferencia de las pruebas unitarias tradicionales, que normalmente son métodos cerrados, las PUT toman cualquier conjunto de parámetros. ¿Es así de sencillo? Sí. A partir de ahí, IntelliTest intentará [generar el conjunto (mínimo) de entradas](input-generation.md) que [cubre complemente](input-generation.md#dynamic-code-coverage) el código accesible desde la prueba.

Las PUT se definen con el atributo personalizado [PexMethod](attribute-glossary.md#pexmethod) de una manera similar a MSTest (o NUnit, xUnit). Las PUT son métodos de instancia agrupados de manera lógica en clases etiquetadas con [PexClass](attribute-glossary.md#pexclass). En el ejemplo siguiente se muestra una PUT sencilla almacenada en la clase **MyPexTest**:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

donde **ReplaceFirstChar** es un método que reemplaza el primer carácter de una cadena:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Desde esta prueba, IntelliTest puede [generar entradas](input-generation.md) automáticamente para una PUT que cubre muchas rutas de ejecución del código probado. Cada entrada que cubre una ruta de ejecución diferente se "serializa" como una prueba unitaria:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Pruebas unitarias parametrizadas genéricas

Las pruebas unitarias parametrizadas pueden ser métodos genéricos. En este caso, el usuario debe especificar los tipos que se han usado para crear una instancia del método mediante [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Permisos para excepciones

IntelliTest proporciona numerosos atributos de validación para ayudar a las excepciones de evaluación de prioridades en excepciones esperadas y excepciones inesperadas.

Las excepciones esperadas generan casos de prueba negativos con la anotación adecuada como **ExpectedException(typeof(*xxx*))**, mientras que las excepciones inesperadas generan casos de prueba con errores.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Los validadores son:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): permite un tipo de excepción concreto desde cualquier lugar
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): permite un tipo de excepción concreto desde un ensamblado especificado
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): permite un tipo de excepción concreto desde un tipo especificado
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): permite un tipo de excepción concreto desde el tipo sometido a prueba

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Pruebas de tipos internos

IntelliTest puede "probar" tipos internos, siempre que pueda verlos. Para que IntelliTest vea los tipos, se agrega el siguiente atributo a su proyecto de prueba o producto mediante los asistentes de IntelliTest de Visual Studio:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Hipótesis y aserciones

Los usuarios pueden usar hipótesis y aserciones para expresar [condiciones previas](#precondition) (hipótesis) y [condiciones posteriores](#postcondition) (aserciones) sobre sus pruebas. Cuando IntelliTest genera un conjunto de valores de parámetro y "explora" el código, puede infringir una hipótesis de la prueba. Cuando eso sucede, no generará una prueba para esa ruta sino que la ignorará de forma automática.

Las aserciones son un concepto muy conocido en los marcos de pruebas unitarias habituales, por lo que IntelliTest ya "entiende" las clases **Assert** integradas proporcionadas por cada marco de prueba admitido. En cambio, la mayoría de los marcos no proporcionan una clase **Assume**. En ese caso, IntelliTest proporciona la clase [PexAssume](static-helper-classes.md#pexassume). Si no quiere usar un marco de pruebas existente, IntelliTest también tiene la clase [PexAssert](static-helper-classes.md#pexassert).

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

En concreto, la hipótesis no NULL puede codificarse como un atributo personalizado:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Condición previa

Una condición previa de un método expresa las condiciones en las que el método se ejecutará correctamente.

Normalmente, la condición previa se aplica comprobando los parámetros y el estado del objeto, y generando **ArgumentException** o **InvalidOperationException** si se infringe.

En IntelliTest, una condición previa de una [prueba unitaria parametrizada](#parameterized-unit-testing) se expresa con [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Condición posterior

Una condición posterior de un método expresa las condiciones que deben incluirse durante y después de la ejecución del método, de manera que se presupone que sus condiciones previas eran válidas inicialmente.

Normalmente, la condición posterior se aplica mediante llamadas a los métodos **Assert**.

Con IntelliTest, una condición posterior de una [prueba unitaria parametrizada](#parameterized-unit-testing) se expresa con [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Errores de pruebas
¿Cuándo se produce un error en un caso de prueba generado?

1. Si no finaliza dentro de los [límites de ruta configurados](exploration-bounds.md), se considera incorrecto a no ser que se establezca la opción [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded).

1. Si la prueba genera **PexAssumeFailedException**, se realiza correctamente. En cambio, normalmente se filtra a no ser que [TestEmissionFilter](exploration-bounds.md#testemissionfilter) se establezca en **All**.

1. Si la prueba infringe una [aserción](#assumptions-and-assertions); por ejemplo, generando una excepción de infracción de aserción de un marco de pruebas unitarias, se produce un error.

Si ninguna de las opciones anteriores produce una decisión, una prueba se realiza correctamente si y solo si no genera una excepción. Las infracciones de aserción se tratan de la misma manera que las excepciones.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Configuración y anulación

Como parte de la integración con marcos de prueba, IntelliTest admite la detección y ejecución de métodos de configuración y anulación.

**Ejemplo**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Lecturas adicionales

* [Prueba para los enlaces de código](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Una prueba para controlarlo todo](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=8).
