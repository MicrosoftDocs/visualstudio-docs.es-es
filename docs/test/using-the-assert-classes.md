---
title: Clases y métodos de prueba MSTest Assert
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d9d02ee375a5b9e6069a94cd7b534b871792088a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962019"
---
# <a name="use-assert-classes-for-unit-testing"></a>Utilice las clases Assert para realizar pruebas unitarias

Utilice las clases Assert del espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> para comprobar la funcionalidad específica. Un método de prueba unitaria utiliza el código de un método en el código de la aplicación, pero solo notifica la corrección del comportamiento del código si se incluyen instrucciones Assert.

## <a name="kinds-of-asserts"></a>Tipos de aserciones

El espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> proporciona varios tipos de clases Assert.

En el método de prueba, puede llamar a cualquier método de la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>, como <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. La clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> tiene muchos métodos para elegir y muchos de ellos tienen varias sobrecargas.

### <a name="compare-strings-and-collections"></a>Comparar cadenas y colecciones

Utilice la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> para comparar colecciones de objetos o comprobar el estado de una colección.

Use la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> para comparar y examinar cadenas. Esta clase contiene una serie de métodos útiles, como <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> y <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Excepciones

La excepción <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> se produce siempre que se produce un error en una prueba. Una prueba produce un error si agota el tiempo, inicia una excepción inesperada o contiene una instrucción Assert que genera un resultado de **error**.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> se inicia siempre que una prueba genera un resultado **no concluyente**. Normalmente, se agrega una instrucción <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> a una prueba de que se sigue trabajando para indicar que aún no está lista para ejecutarse.

> [!NOTE]
> Una estrategia alternativa consiste en marcar una prueba que no está lista para ejecutarse con el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>. Pero esto tiene la desventaja de que no puede generar fácilmente un informe sobre el número de pruebas que no se implementan.

Si escribe una nueva clase de excepción de aserción, hereda de la clase base <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> para facilitar identificar la excepción como un error de aserción en lugar de una excepción inesperada iniciada desde el código de producción o de prueba.

Aplique el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> en un método de prueba cuando quiera que dicho método compruebe que una excepción que espera que inicie un método en el código de la aplicación se inicie realmente.

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)