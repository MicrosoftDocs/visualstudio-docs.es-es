---
title: Herramientas de prueba
description: Descubra cómo las herramientas de prueba de Visual Studio pueden ayudarle a usted y a su equipo a desarrollar y mantener altos estándares de excelencia de código.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e2224ffc1776a15453d1382872c2d3f5a9e86c3c
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760957"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Primer vistazo a las herramientas de prueba de Visual Studio

Las herramientas de prueba de Visual Studio pueden ayudarle a usted y a su equipo a desarrollar y mantener altos estándares de excelencia de código.

> [!NOTE]
> Las pruebas unitarias están disponibles en todas las ediciones de Visual Studio. Otras herramientas de pruebas, como Live Unit Testing e IntelliTest, solo están disponibles en la edición Visual Studio Enterprise. Para obtener más información sobre las ediciones, vea [Comparar los IDE de Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Explorador de pruebas

La ventana del **Explorador de pruebas** ayuda a los desarrolladores a crear, administrar y ejecutar pruebas unitarias. Puede usar el marco de pruebas unitarias de Microsoft o uno de los marcos de terceros y de código abierto.

::: moniker range="vs-2017"
![Explorador de pruebas de Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range=">=vs-2019"
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

> [!NOTE]
> Live Unit Testing solo está disponible en la edición Enterprise y únicamente se admite para código .NET.

## <a name="intellitest"></a>IntelliTest

IntelliTest genera automáticamente pruebas unitarias y datos de prueba para el código administrado. IntelliTest mejora la cobertura y reduce drásticamente el esfuerzo de crear y mantener pruebas unitarias para código nuevo o existente.

![Funcionamiento de IntelliTest](media/devtest-intellitest.png)

> [!NOTE]
> IntelliTest solo está disponible en la edición Enterprise. Se admite para código de C# que tenga como destino .NET Framework. En estos momentos, no se admite .NET Core ni .NET Standard.

* [Generar pruebas unitarias para el código con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest: una prueba para controlarlo todo](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Manual de referencia de IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Cobertura de código

La [cobertura de código](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) determina qué proporción del código del proyecto se está probando realmente mediante pruebas automatizadas como pruebas unitarias. Para restringir con eficacia los errores, las pruebas deberían ensayar o "cubrir" una proporción considerable del código.

> [!NOTE]
> La cobertura de código solo está disponible en la edición Enterprise.

El análisis de cobertura de código puede aplicarse al código administrado y no administrado (nativo).

La cobertura de código es una opción al ejecutar métodos de prueba mediante el Explorador de pruebas. La tabla de salida muestra el porcentaje de código que se ejecuta en cada ensamblado, clase y método. Además, el editor de código fuente muestra qué código se ha probado.

* [Utilizar cobertura de código para determinar la cantidad de código que se está probando](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Pruebas unitarias, cobertura de código y análisis de clon de código con Visual Studio (Lab)](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Personalizar el análisis de cobertura de código](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) ayuda a aislar el código que se está probando mediante la sustitución de otros elementos de la aplicación con código auxiliar (stub) o correcciones de compatibilidad (shim).

> [!NOTE]
> Microsoft Fakes solo está disponible en la edición Enterprise y únicamente se admite para código .NET.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Pruebas de interfaz de usuario con UI codificada y Selenium

Las pruebas de UI codificada proporcionan una manera de crear pruebas completamente automatizadas con el fin de validar la funcionalidad y el comportamiento de la interfaz de usuario de la aplicación. Pueden automatizar las pruebas de la interfaz de usuario en varias tecnologías, incluidas las aplicaciones de UWP basadas en XAML, las aplicaciones del explorador y las de SharePoint.

> [!NOTE]
> La interfaz de usuario codificada es una característica en desuso.

Tanto si elige las pruebas de IU codificadas más convenientes como las pruebas genéricas de interfaz de usuario basadas en exploradores con Selenium, Visual Studio proporciona todas las herramientas que necesita.

![Pruebas de interfaz de usuario con UI codificada](media/devtest-codeduitest.png)

* [Usar la automatización de la interfaz de usuario para probar el código](use-ui-automation-to-test-your-code.md)
* [Comenzar a crear, modificar y mantener una prueba de UI codificada](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Comprobación de aplicaciones para UWP con pruebas automatizadas de IU](test-uwp-app-with-coded-ui-test.md)
* [Introducción a las pruebas de UI codificadas con Visual Studio Enterprise (Lab)](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>Escenarios relacionados

* [Exploratory & manual testing (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true) [Pruebas exploratorias y manuales (Azure Test Plans)]
* [Load testing (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true) [Prueba de carga (Azure Test Plans)]
* [Continuous testing (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) [Prueba continua (Azure Test Plans)]
* [Herramientas de análisis de código](../code-quality/code-analysis-for-managed-code-overview.md)
