---
title: Herramientas de prueba
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b68793e512cdb367375cc9f27d61ae5a85e4f078
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653279"
---
# <a name="testing-tools-in-visual-studio"></a>Herramientas de prueba de Visual Studio

Las herramientas de prueba de Visual Studio pueden ayudarle a usted y a su equipo a desarrollar y mantener altos estándares de excelencia de código.

> [!NOTE]
> Las pruebas unitarias están disponibles en todas las ediciones de Visual Studio. Otras herramientas de pruebas, como Live Unit Testing, IntelliTest y pruebas automatizadas de IU, solo están disponibles en la edición Visual Studio Enterprise. Para obtener más información sobre las ediciones, vea [Comparar los IDE de Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Explorador de pruebas

La ventana del **Explorador de pruebas** ayuda a los desarrolladores a crear, administrar y ejecutar pruebas unitarias. Puede usar el marco de pruebas unitarias de Microsoft o uno de los marcos de terceros y de código abierto.

::: moniker range="vs-2017"
![Explorador de pruebas de Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Explorador de pruebas de Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Introducción a las pruebas unitarias](unit-test-your-code.md)
* [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md)
* [Preguntas más frecuentes sobre el Explorador de pruebas](test-explorer-faq.md)
* [Instalar marcos de prueba unitaria de terceros](install-third-party-unit-test-frameworks.md)

Visual Studio también puede ampliarse y abre la puerta a adaptadores de pruebas de terceros como NUnit y xUnit.net. Además, la función de clon de código está vinculada con proporcionar software de alta calidad ayudándole a identificar bloques de código similar semánticamente que pueden ser candidatos para refactorización o correcciones de errores comunes.

![Integración de pruebas de terceros](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) ejecuta automáticamente pruebas unitarias en segundo plano y muestra una representación gráfica de los resultados de la prueba y la cobertura de código en el editor de código de Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest genera automáticamente pruebas unitarias y datos de prueba para el código administrado. IntelliTest mejora la cobertura y reduce drásticamente el esfuerzo de crear y mantener pruebas unitarias para código nuevo o existente.

![Funcionamiento de IntelliTest](media/devtest-intellitest.png)

* [Generar pruebas unitarias para el código con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest: una prueba para controlarlo todo](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Manual de referencia de IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Cobertura de código

La [cobertura de código](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) determina qué proporción del código del proyecto se está probando realmente mediante pruebas automatizadas como pruebas unitarias. Para restringir con eficacia los errores, las pruebas deberían ensayar o "cubrir" una proporción considerable del código.

El análisis de cobertura de código puede aplicarse al código administrado y no administrado (nativo).

La cobertura de código es una opción al ejecutar métodos de prueba mediante el Explorador de pruebas. La tabla de salida muestra el porcentaje de código que se ejecuta en cada ensamblado, clase y método. Además, el editor de código fuente muestra qué código se ha probado.

* [Utilizar cobertura de código para determinar la cantidad de código que se está probando](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Pruebas unitarias, cobertura de código y análisis de clon de código con Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personalizar el análisis de cobertura de código](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) ayuda a aislar el código que se está probando mediante la sustitución de otros elementos de la aplicación con código auxiliar (stub) o correcciones de compatibilidad (shim).

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Pruebas de interfaz de usuario con UI codificada y Selenium

Las pruebas de UI codificada proporcionan una manera de crear pruebas completamente automatizadas con el fin de validar la funcionalidad y el comportamiento de la interfaz de usuario de la aplicación. Pueden automatizar las pruebas de la interfaz de usuario en varias tecnologías, incluidas las aplicaciones de UWP basadas en XAML, las aplicaciones del explorador y las de SharePoint.

Tanto si elige las pruebas de IU codificadas más convenientes como las pruebas genéricas de interfaz de usuario basadas en exploradores con Selenium, Visual Studio proporciona todas las herramientas que necesita.

![Pruebas de interfaz de usuario con UI codificada](media/devtest-codeduitest.png)

* [Usar la automatización de la interfaz de usuario para probar el código](use-ui-automation-to-test-your-code.md)
* [Comenzar a crear, modificar y mantener una prueba de UI codificada](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Comprobación de aplicaciones para UWP con pruebas automatizadas de IU](test-uwp-app-with-coded-ui-test.md)
* [Introducción a las pruebas de UI codificadas con Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Pruebas de carga

La [prueba de carga](../test/quickstart-create-a-load-test-project.md) simula la carga en una aplicación de servidor mediante la ejecución de pruebas unitarias y pruebas de rendimiento web.

## <a name="related-scenarios"></a>Escenarios relacionados

* [Exploratory & manual testing (Azure Test Plans)](/azure/devops/test/index?view=vsts) [Pruebas exploratorias y manuales (Azure Test Plans)]
* [Load testing (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts) [Prueba de carga (Azure Test Plans)]
* [Continuous testing (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) [Prueba continua (Azure Test Plans)]
* [Herramientas de análisis de código](../code-quality/code-analysis-for-managed-code-overview.md)
