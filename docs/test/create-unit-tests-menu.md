---
title: Crear códigos auxiliares de métodos de pruebas unitarias en Visual Studio | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1620612bc27c41fcebfcc28b2844b3022fa482fa
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Crear códigos auxiliares de método de pruebas unitarias con el comando Crear pruebas unitarias

El comando **Crear pruebas unitarias** de Visual Studio proporciona la capacidad de crear códigos auxiliares de método de pruebas unitarias. Esta característica permite una configuración sencilla de un proyecto de prueba, la clase de prueba y el código auxiliar de método de pruebas de su interior.

## <a name="availability-and-extensions"></a>Disponibilidad y extensiones

El comando de menú **Crear pruebas unitarias**:

* Está disponible en las ediciones Community, Professional y Enterprise de Visual Studio 2015 y versiones posteriores.

* Solo admite código de C# que tenga como destino .NET Framework.

* Es extensible y admite la emisión de pruebas en formato MSTest, MSTest V2, NUnit y xUnit.

## <a name="get-started"></a>Primeros pasos

Para comenzar, seleccione un método, un tipo o un espacio de nombres en el editor de código del proyecto que quiere probar, abra el menú contextual y pulse **Crear pruebas unitarias**. Esto abre el cuadro de diálogo **Crear pruebas unitarias** donde pueden seleccionarse las opciones de creación para las nuevas pruebas unitarias.

![Usar el comando Crear pruebas unitarias](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Establecer los rasgos de las pruebas unitarias

Si planea ejecutar estas pruebas como parte del proceso de automatización de pruebas, puede considerar la posibilidad de tener la prueba creada en otro proyecto de prueba (la segunda opción en el cuadro de diálogo anterior) y establecer los rasgos de las pruebas unitarias para la prueba unitaria. Esto le permitirá incluir o excluir más fácilmente estas pruebas específicas como parte de una integración continua o de una canalización de implementación continua. Los rasgos se establecen agregando metadatos a las pruebas unitarias directamente, como se muestra a continuación.

![Establecer los rasgos de las pruebas unitarias](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Usar marcos de pruebas unitarias de terceros

Con Visual Studio, puede tener pruebas unitarias creadas fácilmente con cualquier marco de pruebas. Para instalar otros marcos de pruebas:

1. Seleccione **Herramientas** > **Extensiones y actualizaciones**.
2. Expanda **En línea** > **Visual Studio Marketplace** > **Herramientas** y, a continuación, elija **Pruebas**.

![Usar marcos de pruebas de terceros](media/createunittestfx.png)

Las extensiones de marcos de pruebas están disponibles en Visual Studio Marketplace:

* [Extensión de NUnit para los generadores de pruebas](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extensión de xUnit.net para los generadores de pruebas](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>¿Cuándo debería usar esta característica?

Use esta característica cada vez que necesite crear pruebas unitarias, pero específicamente cuando esté probando código existente que tenga muy poca o ninguna cobertura de prueba, y ninguna documentación. En otras palabras, donde exista una especificación de código limitada o inexistente. Implementa de manera eficaz un enfoque similar a las [pruebas unitarias inteligentes](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) que caracterizan el comportamiento observado del código.

En cambio, esta característica se aplica igualmente a la situación en la que el desarrollador comienza escribiendo código y la usa para arrancar la disciplina de pruebas unitarias. Dentro del flujo de codificación, el desarrollador puede que quiera crear rápidamente un código auxiliar de método de pruebas unitarias (con una clase de prueba y un proyecto de prueba adecuados) para un fragmento de código concreto.

## <a name="see-also"></a>Vea también

- [Crear códigos auxiliares de método de pruebas unitarias con "Crear pruebas unitarias"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Entradas del blog de pruebas unitarias](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
