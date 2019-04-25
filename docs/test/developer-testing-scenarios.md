---
title: Herramientas de prueba para desarrolladores
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1cc43bfeb66792d2d8ff5a736d957740f62c5ff
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416219"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Herramientas de prueba para desarrolladores, escenarios y funciones

Conserve el estado del código con las pruebas unitarias. Visual Studio proporciona una amplia variedad de herramientas y técnicas eficaces para que los desarrolladores las usen al probar aplicaciones.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Evitar regresiones y obtener la cobertura de código con IntelliTest

En los conjuntos de pruebas unitarias tradicionales, cada caso de prueba representa un escenario de uso ejemplar, y las aserciones representan la relación entre la entrada y la salida.  Comprobar algunos de dichos escenarios podría ser suficiente, pero los desarrolladores con experiencia saben que existen errores incluso en código totalmente probado, cuando las entradas correctas pero sin probar provocan respuestas incorrectas.

Mejore la cobertura y evite regresiones con IntelliTest. IntelliTest reduce drásticamente el esfuerzo de crear y mantener pruebas unitarias para código nuevo o existente.

![Funcionamiento de IntelliTest](media/devtest-intellitest.png)

* [Introducción a IntelliTest con Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest: una prueba para controlarlo todo](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Vídeos de IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Introducción a IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Manual de referencia de IntelliTest](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Pruebas de interfaz de usuario con UI codificada y Selenium

Pruebe su interfaz de usuario (UI) con las mejores pruebas de interfaz de usuario de la clase y la comunidad. Las pruebas de UI codificada proporcionan una manera de crear pruebas completamente automatizadas con el fin de validar la funcionalidad y el comportamiento de la interfaz de usuario de la aplicación. Pueden automatizar las pruebas de la interfaz de usuario en varias tecnologías, incluidas las aplicaciones de UWP basadas en XAML, las aplicaciones del explorador y las de SharePoint.

Tanto si elige las pruebas automatizadas de IU o pruebas genéricas de interfaz de usuario basadas en exploradores con Selenium, Visual Studio proporciona todas las herramientas que necesita.

![Pruebas de interfaz de usuario con UI codificada](media/devtest-codeduitest.png)

* [Usar la automatización de la interfaz de usuario para probar el código](use-ui-automation-to-test-your-code.md)
* [Comenzar a crear, modificar y mantener una prueba de UI codificada](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Comprobación de aplicaciones para UWP con pruebas automatizadas de IU](test-uwp-app-with-coded-ui-test.md)
* [Introducción a las pruebas de UI codificadas con Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Pruebas unitarias eficaces con la cobertura de código de Visual Studio

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede usar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar o "cubrir" una proporción considerable del código.

El análisis de cobertura de código puede aplicarse al código administrado y no administrado (nativo).

La cobertura de código es una opción al ejecutar métodos de prueba mediante el Explorador de pruebas. La tabla de salida muestra el porcentaje de código que se ejecuta en cada ensamblado, clase y método. Además, el editor de código fuente muestra qué código se ha probado.

* [Utilizar cobertura de código para determinar la cantidad de código que se está probando](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Pruebas unitarias, cobertura de código y análisis de clon de código con Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personalizar el análisis de cobertura de código](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Explorador de pruebas

El **Explorador de pruebas** ayuda a los desarrolladores a crear, administrar y ejecutar pruebas unitarias.

![Explorador de pruebas de Visual Studio](media/devtest-testexplorer.png)

* [Introducción a las pruebas unitarias](unit-test-your-code.md)
* [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md)
* [Preguntas más frecuentes sobre el Explorador de pruebas](test-explorer-faq.md)
* [Instalar marcos de prueba unitaria de terceros](install-third-party-unit-test-frameworks.md)

Visual Studio también puede ampliarse y abre la puerta a adaptadores de pruebas de terceros como NUnit y xUnit.net. Además, la función de clon de código está vinculada con proporcionar software de alta calidad ayudándole a identificar bloques de código similar semánticamente que pueden ser candidatos para refactorización o correcciones de errores comunes.

![Integración de pruebas de terceros](media/devtest-thirdparty.png)

## <a name="see-also"></a>Vea también

* [Introducción a las pruebas unitarias](getting-started-with-unit-testing.md)
* [Acelerar la ejecución de pruebas unitarias en Team Foundation Server](https://devblogs.microsoft.com/devops/speeding-up-unit-test-execution-in-tfs/)
* [Ejecución de pruebas unitarias contextuales y paralelas](https://devblogs.microsoft.com/devops/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Pruebas unitarias, cobertura de código y análisis de clon de código con Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
