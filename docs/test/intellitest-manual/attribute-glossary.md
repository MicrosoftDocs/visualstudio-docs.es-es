---
title: Glosario de atributos | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 00d8b24d26237a3c7b4130eba4614b5ea7b7eccd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307002"
---
# <a name="attribute-glossary"></a>Glosario de atributos

## <a name="attributes-by-namespace"></a>Atributos por espacio de nombres

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Este atributo declara que el valor controlado no puede ser **null**. Puede adjuntarse a:

* un **parámetro** de un método de prueba parametrizado

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* un **campo**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* un **tipo**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

También puede adjuntarse a un ensamblado de prueba, a un accesorio de prueba o a un método de prueba; en este caso, el primer argumento debe indicar en qué campo o tipo se aplican las hipótesis. Cuando el atributo se aplica a un tipo, se aplica a todos los campos con este tipo formal.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Este atributo marca una clase que contiene *exploraciones*. Es el equivalente del elemento **TestClassAttribute** de MSTest (o del elemento **TestFixtureAttribute** de NUnit). Este atributo es opcional.

Las clases marcadas con [PexClass](#pexclass) deben ser *construibles de manera predeterminada*:

* tipo exportado públicamente
* constructor predeterminado
* no abstracto

Si la clase no cumple esos requisitos, se notifica un error y se produce un error en la exploración.

También es muy recomendable hacer que esas clases sean **parciales**, de manera que IntelliTest pueda generar nuevas pruebas que formen parte de la clase, pero en un archivo independiente. Este enfoque soluciona muchos problemas debido a la [visibilidad](input-generation.md#visibility) y es una técnica típica en C#.

**Conjunto adicional y categorías**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Especificar el tipo en la prueba**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

La clase puede contener métodos anotados con [PexMethod](#pexmethod). IntelliTest también entiende los [métodos de configuración y anulación](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Este atributo proporciona una tupla de tipo para crear instancias de una [prueba unitaria parametrizada genérica](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Este atributo marca un método como una [prueba unitaria parametrizada](test-generation.md#parameterized-unit-testing).
El método debe residir dentro de una clase marcada con el atributo [PexClass](#pexclass).

IntelliTest generará pruebas sin parámetros tradicionales, que llaman a la [prueba unitaria parametrizada](test-generation.md#parameterized-unit-testing) con diferentes parámetros.

La prueba unitaria parametrizada:

* debe ser un método de instancia
* debe ser [visible](input-generation.md#visibility) para la clase de prueba en la que se colocan las pruebas generadas según la [cascada de configuración](settings-waterfall.md)
* puede tomar cualquier número de parámetros
* puede ser genérica

**Ejemplo**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Más información](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Este atributo puede establecerse en el nivel de ensamblado para invalidar los valores de configuración predeterminados de todas las exploraciones.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Este atributo especifica un ensamblado que se está probando mediante el proyecto de prueba actual.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Este atributo se usa para especificar un ensamblado que se va a instrumentar.

**Ejemplo**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Este atributo le indica a IntelliTest que puede usar un tipo particular para crear instancias de interfaces o tipos base (abstractos).

**Ejemplo**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Si este atributo está adjunto a [PexMethod](#pexmethod) (o a [PexClass](#pexclass), cambia la lógica de IntelliTest predeterminada que indica cuando se produce un error en las pruebas. La prueba no se considerará incorrecta, aunque genere la excepción especificada.

**Ejemplo**

La prueba siguiente especifica que el constructor de **Stack** puede generar **ArgumentOutOfRangeException**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

El filtro se adjunta a un accesorio como se indica a continuación (también puede definirse en el nivel de prueba o ensamblado):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Más información](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Más información](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Más información](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
