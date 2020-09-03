---
title: Pruebas unitarias para métodos genéricos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 49
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2619e975dbfd22d96db2cc382a7cebbf04a05223
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657274"
---
# <a name="unit-tests-for-generic-methods"></a>Pruebas unitarias para métodos genéricos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede generar pruebas unitarias para métodos genéricos exactamente como lo hace para otros métodos, tal y como se describe en [Cómo: Crear y ejecutar una prueba unitaria](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48). Las secciones siguientes proporcionan información y ejemplos de creación de pruebas unitarias para métodos genéricos.

## <a name="type-arguments-and-type-constraints"></a>Argumentos de tipo y restricciones de tipo
 Cuando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera una prueba unitaria para una clase genérica, como `MyList<T>`, genera dos métodos: un asistente genérico y un método de prueba. Si `MyList<T>` tiene una o más restricciones de tipo, el argumento de tipo debe cumplir todas las restricciones de tipo. Para asegurarse de que el código genérico en prueba funciona según lo esperado para todas las entradas permitidas, el método de prueba llama al método del asistente genérico con todas las restricciones que se desean probar.

## <a name="examples"></a>Ejemplos
 Los ejemplos siguientes ilustran las pruebas unitarias para métodos genéricos:

- [Editar el código de prueba generado](#EditingGeneratedTestCode). Este ejemplo tiene dos secciones: Código de prueba generado y Código de prueba editado. Muestra cómo modificar el código de prueba sin formato que se genera a partir de un método genérico en un método de prueba útil.

- [Usar una restricción de tipo](#TypeConstraintNotSatisfied). En este ejemplo se muestra una prueba unitaria para un método genérico que utiliza una restricción de tipo. En este ejemplo no se cumple la restricción de tipo.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Ejemplo 1: editar el código de prueba generado
 El código de prueba de esta sección prueba un método de código en prueba denominado `SizeOfLinkedList()`. Este método devuelve un entero que especifica el número de nodos en la lista vinculada.

 El primer ejemplo de código, en la sección Código de prueba generado, muestra el código de prueba sin editar, tal y como lo generó Visual Studio Enterprise. El segundo ejemplo, en la sección Código de prueba editado, muestra cómo puede hacer que pruebe el funcionamiento del método SizeOfLinkedList para dos tipos de datos diferentes, `int` y `char`.

 Este código ilustra dos métodos:

- un método del asistente de prueba, `SizeOfLinkedListTestHelper<T>()`. De forma predeterminada, un método del asistente de prueba incluye "TestHelper" en su nombre.

- un método de prueba, `SizeOfLinkedListTest()`. Cada método de prueba se marca con el atributo TestMethod.

#### <a name="generated-test-code"></a>Código de prueba generado
 El código de prueba siguiente se generó a partir del método `SizeOfLinkedList()`. Dado que se trata de la prueba generada sin editar, debe modificarse para probar correctamente el método SizeOfLinkedList.

```
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

 En el código anterior, el parámetro de tipo genérico es `GenericParameterHelper`. Dado que puede editarlo para proporcionar tipos de datos específicos, tal y como se muestra en el ejemplo siguiente, podría ejecutar la prueba sin modificar esta instrucción.

#### <a name="edited-test-code"></a>Código de prueba editado
 En el código siguiente, el método de prueba y el método del asistente de prueba se han editado para que prueben correctamente el método de código en prueba `SizeOfLinkedList()`.

##### <a name="test-helper-method"></a>Método del asistente de prueba
 El método del asistente de prueba realiza los pasos siguientes, que corresponden a las líneas del código con las etiquetas del paso 1 al paso 5.

1. Cree una lista vinculada genérica.

2. Anexe cuatro nodos a la lista vinculada. El tipo de datos del contenido de estos nodos es desconocido.

3. Asigne el tamaño esperado de la lista vinculada a la variable `expected`.

4. Calcule el tamaño real de la lista vinculada y asígnelo a la variable `actual`.

5. Compare `actual` con `expected` en una instrucción Assert. Si el tamaño real no es igual al esperado, se produce un error en la prueba.

##### <a name="test-method"></a>Método de prueba
 El método de prueba se compila en el código que se llama al ejecutar la prueba denominada SizeOfLinkedListTest. Realiza los pasos siguientes, que corresponden a las líneas del código con las etiquetas del paso 6 y el paso 7.

1. Especifique `<int>` al llamar el método del asistente de prueba para comprobar que la prueba funciona para las variables `integer`.

2. Especifique `<char>` al llamar el método del asistente de prueba para comprobar que la prueba funciona para las variables `char`.

```

public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Cada vez que se ejecuta la prueba SizeOfLinkedListTest, se llama dos veces a su método TestHelper. La instrucción Assert debe evaluarse como true todas las veces para que la prueba se supere. Si se produce un error en la prueba, es posible que no quede claro si fue la llamada que especificó `<int>` o la llamada que especificó `<char>` la que provocó el error. Para encontrar la respuesta, puede examinar la pila de llamadas o establecer puntos de interrupción en el método de prueba y luego depurar mientras se ejecuta la prueba. Para obtener más información, vea [Cómo: depurar mientras se ejecuta una prueba en una solución de ASP.net](https://msdn.microsoft.com/library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Ejemplo 2: usar una restricción de tipo
 En este ejemplo se muestra una prueba unitaria para un método genérico que usa una restricción de tipo que no se cumple. La primera sección muestra código del proyecto de código en prueba. Se resalta la restricción de tipo.

 La segunda sección muestra el código del proyecto de prueba.

#### <a name="code-under-test-project"></a>Proyecto de código en prueba

```
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>Proyecto de prueba
 Al igual que con todas las pruebas unitarias recién generadas, debe agregar instrucciones Assert no dudosas a esta prueba unitaria para que devuelva resultados útiles. No las agregue al método marcado con el atributo TestMethod, sino al método "TestHelper", que en esta prueba se denomina `DataTestHelper<T>()`.

 En este ejemplo, el parámetro de tipo genérico `T` tiene la restricción `where T : Employee`. Esta restricción no se cumple en el método de prueba. Por lo tanto, el método `DataTest()` contiene una instrucción Assert que le advierte de la necesidad de proporcionar la restricción de tipo que se ha colocado en `T`. El mensaje de esta instrucción Assert quede como sigue: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

 En otras palabras, cuando llame al método `DataTestHelper<T>()` desde el método de prueba `DataTest()`, debe pasar un parámetro de tipo `Employee` o una clase derivada de `Employee`.

 `using ClassLibrary2;`

 `using Microsoft.VisualStudio.TestTools.UnitTesting;`

 `namespace TestProject1`

```
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>Consulte también
 [Anatomía de una](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) prueba unitaria probar [el código](../test/unit-test-your-code.md)
