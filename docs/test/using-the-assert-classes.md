---
title: Clases y métodos de prueba MSTest Assert
description: Aprenda a usar instrucciones Assert para probar la corrección del comportamiento del código durante una prueba unitaria del código de la aplicación.
ms.custom: SEO-VS-2020
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 1f064ee1ca41aab19e19fa6006d983a76ed006d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946207"
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

Para comprobar que una excepción que espera que inicie un método en el código de la aplicación se inicia realmente, use el método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
