---
title: "Utilizar las clases Assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert (clases)"
  - "Assert (instrucciones)"
  - "pruebas unitarias, instrucciones Assert"
  - "pruebas unitarias, clases Assert"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Utilizar las clases Assert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilice las clases Assert del espacio de nombres UnitTestingFramework para comprobar una funcionalidad específica.  Un método de prueba unitaria utiliza el código de un método en el código de desarrollo, pero lo informa de la corrección del comportamiento del código únicamente si se incluyen instrucciones assert.  
  
## Tipos de clases Assert  
 El espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> proporciona varios tipos de clases Assert:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 En su método de prueba, puede llamar a la cantidad de métodos de la clase Assert que desee, como Assert.AreEqual\(\).  La clase Assert tiene numerosos métodos entre los que elegir y muchos de esos métodos tienen varias sobrecargas.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Utilice la clase CollectionAssert para comparar colecciones de objetos y para comprobar el estado de una o más colecciones.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Utilice la clase StringAssert para comparar cadenas.  Esta clase contiene una variedad de métodos útiles como StringAssert.Contains, StringAssert.Matches y StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 La excepción AssertFailedException se inicia siempre que una prueba produce errores.  Una prueba produce errores si agota el tiempo de espera, si inicia una excepción inesperada, o si contiene una instrucción Assert que genera un resultado de error.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 AssertInconclusiveException se inicia siempre que una prueba genera un resultado de No concluyente.  Normalmente, se agrega una instrucción Assert.Inconclusive a una prueba con la que todavía se está trabajando, para indicar que no está lista para ejecutarse.  
  
> [!NOTE]
>  Una estrategia alternativa sería marcar una prueba que no está lista para ejecutarse con el atributo Ignore.  Sin embargo, esto tiene la desventaja de que no es fácil generar un informe sobre el número de pruebas que no se han implementado todavía.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Si escribe una nueva clase de excepciones Assert, si se hace que esa clase herede de la clase base UnitTestAssertException, será más fácil identificar la excepción como error de aserción en lugar de excepción inesperada iniciada desde la prueba o el código de producción.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Represente un método de prueba con el atributo ExpectedExceptionAttribute cuando desee que el método de prueba compruebe si una excepción que espera que ser iniciada por un método de su código de desarrollo realmente se inicia en ese método.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Crear y ejecutar pruebas unitarias para código existente](http://msdn.microsoft.com/es-es/e8370b93-085b-41c9-8dec-655bd886f173)