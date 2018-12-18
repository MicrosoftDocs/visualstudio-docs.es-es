---
title: clases del asistente estáticas | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5c635c8fb3def61b8278b7b7c4b66aa196d82b8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000482"
---
# <a name="static-helper-classes"></a>clases del asistente estáticas

IntelliTest proporciona un conjunto de clases del asistente estáticas que pueden usarse al crear [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): se usa para definir hipótesis en las entradas, y es útil para filtrar las entradas no deseadas.
* [PexAssert](#pexassert): es una clase de aserción sencilla que se usa si su marco de pruebas no proporciona una.
* [PexChoose](#pexchoose): un flujo de entradas de prueba adicionales que administra IntelliTest.
* [PexObserve](#pexobserve): registra valores concretos y, opcionalmente, los valida en el código generado.

Algunas clases le permiten interactuar con el motor de razonamiento de IntelliTest en un nivel bajo:

* [PexSymbolicValue](#pexsymbolicvalue): utilidades para inspeccionar o modificar restricciones simbólicas en variables.

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Una clase estática que se usa para expresar hipótesis, como [condiciones previas](test-generation.md#precondition), en [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing). Los métodos de esta clase se puede usar para filtrar entradas de prueba no deseadas.

Si la condición que se presupone no se mantiene en alguna entrada de prueba, se genera **PexAssumeFailedException**. Esto provocará que la prueba se ignore de forma automática.

**Ejemplo**

La siguiente prueba parametrizada no considerará **j=0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Comentarios**

El código anterior es casi equivalente a:

```csharp
     if (j==0)
          return;
```

excepto que **PexAssume** con errores no produce ningún caso de prueba. En el caso de una instrucción **if**, IntelliTest genera un caso de prueba independiente para cubrir la rama **then** de la instrucción **if**.

**PexAssume** también contiene clases anidadas especializadas para hipótesis en cadenas, matrices y colecciones.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Una clase estática que se usa para expresar aserciones, como [condiciones posteriores](test-generation.md#postcondition), en [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing).

Si la condición declarada no se mantiene en alguna entrada de prueba, se genera **PexAssertFailedException**, que producirá errores en la prueba.

**Ejemplo**

Lo que se muestra a continuación declara que el valor absoluto de un entero es positivo:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Una clase estática que proporciona valores de entrada auxiliares para una prueba, que se pueden usar para implementar [objetos ficticios parametrizados](input-generation.md#parameterized-mocks).

La clase **PexChoose** no ayuda a determinar si una prueba se supera o produce un error con unos valores de entrada concretos. **PexChoose** simplemente proporciona valores de entrada, a los que también se hace referencia como *opciones*. El usuario sigue siendo el que decide si quiere restringir los valores de entrada y escribir aserciones que definan si una prueba finaliza con éxito o produce error.

**Modos de funcionamiento**

La clase **PexChoose** puede funcionar de dos modos:

* Mientras IntelliTest está realizando un análisis simbólico de la prueba y el código probado durante la [generación de entradas](input-generation.md), el selector devuelve valores arbitrarios e IntelliTest realiza un seguimiento de cómo se usa cada valor en la prueba y en el código probado. IntelliTest generará valores relevantes para desencadenar diferentes rutas de ejecución en la prueba y en el código probado.

* El código generado para los casos de prueba concretos configura el proveedor de opciones de manera específica, de manera que volver a ejecutar dicho caso de prueba hará que las opciones específicas desencadenen una ruta de ejecución concreta.

**Uso**

* Simplemente llame a **PexChoose.Value** para generar un valor nuevo:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Una clase estática para registrar los valores con nombre.

Cuando IntelliTest explora el código, **PexObserve** se usa para registrar valores calculados con sus representaciones de cadena con formato. Los valores están asociados con nombres únicos.

```csharp
PexObserve.Value<string>("result", result);
```

**Ejemplo**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}


// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a); 
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Una clase estática usada para ignorar restricciones en parámetros, y para imprimir la información simbólica asociada con los valores.

**Uso**

Normalmente, IntelliTest intenta cubrir todas las rutas de ejecución del código durante la ejecución. En cambio, especialmente al calcular condiciones de hipótesis y aserción, no debe explorar todos los casos posibles.

**Ejemplo**

En este ejemplo se muestra la implementación del método **PexAssume.Arrays.ElementsAreNotNull**. En el método, ignora las restricciones sobre la longitud del valor de la matriz para evitar que IntelliTest intente generar tamaños diferentes de matriz. Las restricciones solo se ignoran aquí. Si el código probado se comporta de manera diferente para las distintas longitudes de la matriz, IntelliTest no puede generar diferentes tamaños de matriz desde las restricciones del código probado.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).