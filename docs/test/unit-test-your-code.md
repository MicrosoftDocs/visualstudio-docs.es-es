---
title: Pruebas unitarias en Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bc69869e8f1cd60bad1f30f6ee9c37ca5d2821bd
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179221"
---
# <a name="unit-test-your-code"></a>Prueba unitaria del código

Las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases de proyectos de C#, Visual Basic y C++.

Las herramientas de pruebas unitarias incluyen:

* **Explorador de pruebas**: puede ejecutar pruebas unitarias y ver los resultados en el **Explorador de pruebas**. Puede utilizar cualquier marco de pruebas unitarias, incluyendo un marco de terceros, que tenga un adaptador para el **Explorador de pruebas**.

* **Marco de pruebas unitarias de Microsoft para código administrado**: el marco de pruebas unitarias de Microsoft para código administrado se instala con Visual Studio y proporciona un marco para probar el código .NET.

* **Marco de pruebas unitarias de Microsoft para C++**: el marco de pruebas unitarias de Microsoft para C++ se instala como parte de la carga de trabajo **Desarrollo para el escritorio con C++**. Proporciona un marco para probar código nativo. También se incluyen los marcos de trabajo de Google Test, Boost.Test y CTest, y hay disponibles adaptadores de terceros si son necesarios para marcos de trabajo de prueba adicionales. Para obtener más información, vea [Writing unit tests for C/C++](../test/writing-unit-tests-for-c-cpp.md) (Escribir pruebas unitarias para C/C++).

* **Herramientas de cobertura de código**: puede determinar la cantidad de código de producto que utilizan las pruebas unitarias a partir de un comando en el Explorador de pruebas.

* **Marco de aislamiento de Microsoft Fakes**: el marco de aislamiento de Microsoft Fakes puede crear clases y métodos de sustitución para el código de producción y de sistema que crean dependencias en el código en pruebas. Cuando se implementan falsos delegados para una función, se controla el comportamiento y el resultado del objeto de dependencia.

También puede crear pruebas [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), que exploran el código .NET para generar datos de prueba y un conjunto de pruebas unitarias. Para cada instrucción en el código, se genera una entrada de prueba que ejecutará esa instrucción. Se lleva a cabo un análisis de caso para cada bifurcación condicional en el código.

## <a name="key-tasks"></a>Tareas clave

Utilice los temas siguientes para facilitar la comprensión y la creación de pruebas unitarias:

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Guías rápidas y tutoriales**: utilice los siguientes temas para aprender a hacer pruebas unitarias en Visual Studio a partir de ejemplos de código.|-   [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Inicio rápido: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Hacer pruebas unitarias con el Explorador de pruebas**: aprenda cómo el Explorador de pruebas puede ayudar a crear pruebas unitarias más productivas y eficaces.|-   [Conceptos básicos de las pruebas unitarias](../test/unit-test-basics.md)<br />-   [Crear un proyecto de prueba unitaria](../test/create-a-unit-test-project.md)<br />-   [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md)|
|**Pruebas unitarias de código administrado:**|-   [Escribir pruebas unitarias para .NET Framework con el Framework de pruebas unitarias de Microsoft para código administrado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Pruebas unitarias de código C++**|-   [Escribir pruebas unitarias para C/C++ con el marco de pruebas unitarias de Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Aislamiento de pruebas unitarias**|-   [Aislar el código en pruebas con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Utilizar cobertura de código para identificar qué proporción del código del proyecto se prueba:** obtenga información sobre la característica de cobertura de código de las herramientas de prueba de Visual Studio.|-   [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Realice análisis de esfuerzo y rendimiento usando pruebas de carga:** puede crear una prueba de carga y agregarle sus pruebas unitarias para ayudar a aislar los problemas de rendimiento y esfuerzo de la aplicación.|-   [Prueba de carga (VSTS)](/vsts/load-test/)|
|**Establezca puertas de calidad:** puede crear puertas de calidad para exigir que las pruebas se ejecuten antes de insertar el código en el repositorio y así garantizar la calidad del código.|-   [Directivas de inserción en el repositorio (VSTS)](/vsts/tfvc/add-check-policies)|
|**Establecer opciones de prueba:** por ejemplo, puede especificar dónde se almacenan los resultados de las pruebas.|[Configurar pruebas unitarias mediante un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentación de referencia de API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> describe el espacio de nombres UnitTesting, que proporciona los atributos, excepciones, aserciones y otras clases que ofrecen compatibilidad para prueba unitaria.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> describe el espacio de nombres UnitTesting.Web, que extiende el espacio de nombres UnitTesting proporcionando compatibilidad para ASP.NET y pruebas unitarias de servicios web.

## <a name="see-also"></a>Vea también

- [Mejorar la calidad del código](../test/improve-code-quality.md)
