---
title: Creación de códigos auxiliares de método de pruebas unitarias
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3edd4694688011722b9975d299bd09cfb3832a9e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665081"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Crear códigos auxiliares de método de pruebas unitarias con el comando Crear pruebas unitarias

El comando **Crear pruebas unitarias** crea códigos auxiliares de método de pruebas unitarias. Esta característica permite una configuración sencilla de un proyecto de prueba, la clase de prueba y el código auxiliar de método de pruebas de su interior.

> [!NOTE]
> El comando de menú **Crear pruebas unitarias** solo está disponible para el código administrado que tiene como destino .NET Framework (pero no .NET Core).

El comando de menú **Crear pruebas unitarias** es extensible y puede utilizarse para generar pruebas de MSTest, MSTest V2, NUnit y xUnit.

## <a name="get-started"></a>Primeros pasos

Para comenzar, seleccione un método, un tipo o un espacio de nombres en el editor de código del proyecto que quiere probar, haga clic con el botón derecho y elija **Crear pruebas unitarias**. Se abre el cuadro de diálogo **Crear pruebas unitarias**, donde puede configurarse cómo se quiere que se creen las pruebas.

![Usar el comando Crear pruebas unitarias](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Establecer los rasgos de las pruebas unitarias

Si planea ejecutar estas pruebas como parte del proceso de automatización de pruebas, puede considerar la posibilidad de crear la prueba en otro proyecto de prueba (la segunda opción del cuadro de diálogo anterior) y establecer los rasgos de las pruebas unitarias para la prueba unitaria. Esto le permite incluir o excluir más fácilmente estas pruebas específicas como parte de una integración continua o de una canalización de implementación continua. Los rasgos se establecen agregando metadatos a las pruebas unitarias directamente, como se muestra a continuación.

![Establecer los rasgos de las pruebas unitarias](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Usar plataformas de pruebas unitarias de terceros

Para generar automáticamente pruebas unitarias de NUnit o xUnit, instale una de estas extensiones de marco de prueba de Visual Studio Marketplace:

* [Extensión de NUnit para generadores de pruebas](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extensión de xUnit.net para generadores de pruebas](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>¿Cuándo debería usar esta característica?

Use esta característica cada vez que necesite crear pruebas unitarias, pero específicamente cuando esté probando código existente que tenga poca o ninguna cobertura de prueba y ninguna documentación. En otras palabras, donde exista una especificación de código limitada o inexistente. Implementa de manera eficaz un enfoque similar a las [pruebas unitarias inteligentes](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) que caracterizan el comportamiento observado del código.

En cambio, esta característica se aplica igualmente cuando un desarrollador comienza escribiendo código y luego lo usa para el arranque de pruebas unitarias. Dentro del flujo de codificación, el desarrollador puede que quiera crear rápidamente un código auxiliar de método de pruebas unitarias (con una clase de prueba y un proyecto de prueba adecuados) para un fragmento de código concreto.

## <a name="see-also"></a>Vea también

- [Crear códigos auxiliares de método de pruebas unitarias con "Crear pruebas unitarias"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Entradas del blog de pruebas unitarias](https://devblogs.microsoft.com/devops/?s=unit+testing)
