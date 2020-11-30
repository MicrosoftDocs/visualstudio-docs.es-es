---
title: Generar pruebas unitarias para el código con IntelliTest
description: IntelliTest explora el código .NET para generar datos de prueba y un conjunto de pruebas unitarias. Aprenda a ejecutar IntelliTest para ver las pruebas que no se superan y corregirlas.
ms.custom: SEO-VS-2020
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5d503d37cfcacace8250da4d3e91221364c66b5c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442474"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Procedimiento: Generación de pruebas unitarias con IntelliTest

IntelliTest explora el código .NET para generar datos de prueba y un conjunto de pruebas unitarias. Para cada instrucción en el código, se genera una entrada de prueba que ejecutará esa instrucción. Se lleva a cabo un análisis de caso para cada bifurcación condicional en el código. Por ejemplo, se analizan las instrucciones `if`, las aserciones y todas las operaciones que pueden producir excepciones. Con este análisis puede generar los datos de pruebas que deben usarse en una prueba unitaria parametrizada para cada método. También crea pruebas unitarias con una cobertura de código elevada.

Cuando ejecuta Intelltest, puede ver fácilmente qué pruebas son las que fallan y agregar cualquier código para corregirlas. Puede seleccionar las pruebas generadas que quiere guardar en un proyecto de prueba para proporcionar un conjunto de regresión. Cuando cambie el código, vuelva a ejecutar IntelliTest para mantener sincronizadas las pruebas generadas con los cambios de código.

## <a name="availability-and-extensions"></a>Disponibilidad y extensiones

Los comandos de menú **Crear IntelliTest** y **Ejecutar IntelliTest**:

* Solo están disponibles en la edición Enterprise de Visual Studio.

* Solo admiten código de C# que tenga como destino .NET Framework.

* Son [extensibles](#extend-framework) y admiten la emisión de pruebas en formato MSTest, MSTest V2, NUnit y xUnit.

* No admiten la configuración x64.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Explorar: use IntelliTest para explorar el código y generar pruebas unitarias

Para generar las pruebas unitarias, los tipos deben ser públicos.

1. Abra la solución en Visual Studio y después abra el archivo de clase que contenga los métodos que quiere probar.

2. Haga clic con el botón derecho en un método y genere las pruebas unitarias para el código del método haciendo clic en **Ejecutar IntelliTest**.

   ![Haga clic con el botón derecho en el método para generar pruebas unitarias](../test/media/runpex.png)

   IntelliTest ejecuta el código muchas veces con diferentes entradas. Cada ejecución se representa en la tabla que muestra los datos de las pruebas entrantes y la salida o excepción resultante.

   ![La ventana de Resultados de exploración se muestra con las pruebas](../test/media/pexexplorationresults.png)

Para generar pruebas unitarias para todos los métodos públicos en una clase, simplemente haga clic con el botón secundario en la clase en lugar del método específico y después elija **Ejecutar IntelliTest**. Use la lista desplegable en la ventana **Resultados de exploración** para visualizar las pruebas unitarias y los datos entrantes para cada método en la clase.

![Seleccione los resultados de las pruebas para ver en la lista](../test/media/selectpextest.png)

En cuanto a las pruebas superadas, compruebe que los resultados de los cuales se informa en la columna de resultados coincidan con sus expectativas con respecto a su código. Si algunas pruebas generan un error, corrija el código según corresponda. Después vuelva a ejecutar IntelliTest para validar las correcciones.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Persistir: guarde las pruebas unitarias como un conjunto de regresión

1. Seleccione las filas de datos que desea guardar con la prueba unitaria parametrizada en un proyecto de pruebas.

     ![Seleccione las pruebas, haga clic con el botón derecho y seleccione Guardar](../test/media/savepextests.png)

     Puede ver el proyecto de prueba y la prueba unitaria parametrizada que se ha creado; las pruebas unitarias individuales correspondientes a cada una de las filas se guardan en el archivo *.g.cs* del proyecto de prueba y, la prueba unitaria parametrizada, en el archivo *.cs* correspondiente. Puede ejecutar las pruebas unitarias y ver los resultados desde el Explorador de pruebas, tal como lo haría con cualquier prueba unitaria que haya creado manualmente.

     ![Abra el archivo de clase en método de prueba para ver la prueba unitaria](../test/media/testmethodpex.png)

     También se agregan al proyecto de pruebas todas las referencias necesarias.

     Si el código del método cambia, vuelva a ejecutar IntelliTest para mantener sincronizadas las pruebas unitarias con los cambios.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Ayudar: use IntelliTest para centrarse en la exploración del código

1. Si el código es más complejo, IntelliTest le facilitará la exploración. Por ejemplo, si un método tiene una interfaz como parámetro y varias clases implementan dicha interfaz, IntelliTest descubre esas clases y notifica una advertencia.

     Vea las advertencias para decidir qué quiere hacer.

     ![Ver advertencias](../test/media/pexviewwarning.png)

2. Tras investigar el código e identificar qué desea probar, puede corregir la advertencia para elegir las clases con las que se debe probar la interfaz.

     ![Haga clic con el botón secundario en la advertencia y seleccione Corregir](../test/media/pexfixwarning.png)

     Esta opción se agrega al archivo *PexAssemblyInfo.cs*.

     `[assembly: PexUseType(typeof(Camera))]`

3. Ahora puede volver a ejecutar IntelliTest para generar una prueba unitaria parametrizada y datos de pruebas, solo con el uso de la clase que corrigió.

     ![Vuelva a ejecutar IntelliTest para generar los datos de prueba](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Especificar: use IntelliTest para validar las propiedades de corrección especificadas en el código

Especifique la relación general entre entradas y salidas que deben validar las pruebas unitarias generadas. Esta especificación se encapsula en un método similar a un método de prueba, aunque está cuantificado de forma universal. Este es el método de prueba unitaria parametrizada. Las aserciones que se realicen deberán resultar válidas para todos los valores de entrada posibles que IntelliTest pueda generar.

## <a name="q--a"></a>Preguntas y respuestas

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>P: ¿Se puede usar IntelliTest para código no administrado?

**R:** No, IntelliTest solo funciona con código administrado.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>P: ¿Cuándo se supera o falla una prueba generada?

**R:** Se supera al igual que otras pruebas unitarias, es decir, si no ocurre ninguna excepción. Falla si se produce un error de aserción o si el código que se prueba detecta una excepción no controlada.

Si tiene una prueba que puede superarse si se detectan determinadas excepciones, puede establecer uno de los siguientes atributos según sus requisitos en el método de prueba, clase de prueba o nivel de ensamblado:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>P: ¿Puedo agregar suposiciones a la prueba unitaria parametrizada?

**R:** Sí. Use suposiciones para especificar los datos de pruebas que no se necesitan para la prueba unitaria para un método específico. Use la clase <xref:Microsoft.Pex.Framework.PexAssume> para agregar hipótesis. Por ejemplo, puede agregar una suposición en que la variable `lengths` no sea nula como esta:

`PexAssume.IsNotNull(lengths);`

Si agrega una suposición y vuelve a ejecutar IntelliTest, pueden eliminarse los datos de pruebas que ya no son relevantes.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>P: ¿Puedo agregar aserciones a la prueba unitaria parametrizada?

**R:** Sí. IntelliTest comprobará que las aserciones de su instrucción sean realmente correctas cuando ejecute las pruebas unitarias. Use la clase <xref:Microsoft.Pex.Framework.PexAssert> o la API de aserción que se incluye en el marco de pruebas para agregar aserciones. Por ejemplo, puede agregar una aserción de que dos variables son iguales.

`PexAssert.AreEqual(a, b);`

Si agrega una aserción y vuelve a ejecutar IntelliTest, este comprobará que su aserción sea válida o, en caso contrario, la prueba fallará.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a> P: ¿puedo generar pruebas unitarias con parámetros sin ejecutar primero IntelliTest?

**A:** Sí, haga clic con el botón secundario en la clase o método y elija **crear IntelliTest**.

![Haga clic con el botón derecho en el editor y elija Crear IntelliTest](../test/media/pexcreateintellitest.png)

Acepte el formato predeterminado para generar las pruebas o cambie la denominación del proyecto y las pruebas. Puede crear un nuevo proyecto de prueba o guardar las pruebas en un proyecto existente.

![Crear IntelliTest con los valores predeterminados de MSTest](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>P: ¿Puedo usar otros marcos de pruebas unitarias con IntelliTest?

**A:** Sí, siga estos pasos para [buscar e instalar otros marcos](../test/install-third-party-unit-test-frameworks.md).
Las extensiones de marcos de pruebas también están disponibles en Visual Studio Marketplace, por ejemplo, [Generador de prueba de NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Después de reiniciar Visual Studio y volver a abrir la solución, haga clic con el botón secundario en la clase o método y elija **Crear IntelliTest**. Seleccione su marco instalado aquí:

![Seleccione otro marco de pruebas unitarias para IntelliTest](../test/media/pexcreateintellitestextensions.png)

A continuación, ejecute IntelliTest para generar pruebas unitarias individuales en sus correspondientes archivos *.g.cs*.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>P: ¿Puedo obtener más información acerca de cómo se generan las pruebas?

**A:** Sí, para obtener una visión general, lea esta [publicación de blog](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
