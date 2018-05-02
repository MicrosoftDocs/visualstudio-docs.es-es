---
title: Uso de las clases Assert para pruebas unitarias en Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2d56477822fa2d965902d9442d47e2c3ab24d656
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="use-the-assert-classes"></a>Usar las clases Assert

Utilice las clases Assert del espacio de nombres UnitTestingFramework para comprobar la funcionalidad específica. Un método de prueba unitaria utiliza el código de un método en el código de desarrollo, pero solo notifica la corrección del comportamiento del código si se incluyen instrucciones Assert.

## <a name="kinds-of-asserts"></a>Tipos de aserciones

 El espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> proporciona varios tipos de clases Assert:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 En el método de prueba, puede llamar a cualquier número de métodos de la clase Assert, como Assert.AreEqual(). La clase Assert tiene muchos métodos para elegir y muchos de ellos tienen varias sobrecargas.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Utilice la clase CollectionAssert para comparar colecciones de objetos y comprobar el estado de una o más colecciones.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Utilice la clase StringAssert para comparar cadenas. Esta clase contiene una variedad de métodos útiles como StringAssert.Contains, StringAssert.Matches y StringAssert.StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 La excepción AssertFailedException se produce siempre que se produce un error en una prueba. Una prueba produce un error si agota el tiempo, inicia una excepción inesperada o contiene una instrucción Assert que genera un resultado de error.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 AssertInconclusiveException se inicia siempre que una prueba genera un resultado no concluyente. Normalmente, se agrega una instrucción Assert.Inconclusive a una prueba de que se sigue trabajando para indicar que aún no está lista para ejecutarse.

> [!NOTE]
> Una estrategia alternativa consiste en marcar una prueba que no está lista para ejecutarse con el atributo Ignore. Sin embargo, esto tiene la desventaja de que no puede generar fácilmente un informe sobre el número de pruebas que quedan por implementar.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Si escribe una nueva clase de excepción de aserción, tener esa clase hereda de la clase base UnitTestAssertException, facilita identificar la excepción como un error de aserción en lugar de una excepción inesperada iniciada desde el código de producción o de prueba.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Decore un método de prueba con el atributo ExpectedExceptionAttribute cuando desee que el método de prueba compruebe que una excepción que espera es iniciada por un método en el código de desarrollo en ese método.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
