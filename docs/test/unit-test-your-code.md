---
title: Tareas y herramientas de pruebas unitarias
description: Obtenga información sobre las herramientas de pruebas unitarias que puede usar para proporcionar a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en el código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 718f5560176f287f237d54a89bd44c831c7f03ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962618"
---
# <a name="unit-test-tools-and-tasks"></a>Tareas y herramientas de pruebas unitarias

Las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases de proyectos de C#, Visual Basic y C++.

Las herramientas de pruebas unitarias incluyen:

* **Explorador de pruebas**&mdash;Ejecute pruebas unitarias y vea los resultados en el **Explorador de pruebas**. Puede utilizar cualquier marco de pruebas unitarias, incluyendo un marco de terceros, que tenga un adaptador para el **Explorador de pruebas**.

* **Marco de pruebas unitarias de Microsoft para código administrado**: el marco de pruebas unitarias de Microsoft para código administrado se instala con Visual Studio y proporciona un marco para probar el código .NET.

* **Marco de pruebas unitarias de Microsoft para C++** : el marco de pruebas unitarias de Microsoft para C++ se instala como parte de la carga de trabajo **Desarrollo para el escritorio con C++** . Proporciona un marco para probar código nativo. También se incluyen los marcos de trabajo de Google Test, Boost.Test y CTest, y hay disponibles adaptadores de terceros si son necesarios para marcos de trabajo de prueba adicionales. Para más información, vea [Escribir pruebas unitarias para C/C++ en Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

* **Herramientas de cobertura de código**: puede determinar la cantidad de código de producto que utilizan las pruebas unitarias a partir de un comando en el Explorador de pruebas.

* **Marco de aislamiento de Microsoft Fakes**: el marco de aislamiento de Microsoft Fakes puede crear clases y métodos de sustitución para el código .NET de producción y de sistema que crean dependencias en el código sometido a prueba. Cuando se implementan falsos delegados para una función, se controla el comportamiento y el resultado del objeto de dependencia.

Para .NET, también puede usar [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) para explorar su código y generar datos de pruebas y una serie de pruebas unitarias. Para cada instrucción en el código, se genera una entrada de prueba que ejecutará esa instrucción. Se lleva a cabo un análisis de caso para cada bifurcación condicional en el código.

## <a name="key-tasks"></a>Tareas clave

Consulte los siguientes artículos para ampliar sus conocimientos de la comprensión y creación de pruebas unitarias:

|Tareas|Temas relacionados|
|-|-----------------------|
|**Inicios rápidos y tutoriales:** Obtenga información sobre las pruebas unitarias en Visual Studio a partir de ejemplos de código.|- [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Tutorial: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Cómo: Agregación de pruebas unitarias a aplicaciones C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Hacer pruebas unitarias con el Explorador de pruebas**: aprenda cómo el Explorador de pruebas puede ayudar a crear pruebas unitarias más productivas y eficaces.|- [Conceptos básicos de prueba unitaria](../test/unit-test-basics.md)<br />- [Crear un proyecto de prueba unitaria](../test/create-a-unit-test-project.md)<br />- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md)|
|**Código de C++ para pruebas unitarias**|- [Escritura de pruebas unitarias para C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Utilizar cobertura de código para identificar qué proporción del código del proyecto se prueba:** obtenga información sobre la característica de cobertura de código de las herramientas de prueba de Visual Studio.|- [Utilizar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Aislamiento de pruebas unitarias**|- [Aislar el código en pruebas con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Análisis de esfuerzo y rendimiento mediante pruebas de carga:** Descubra cómo puede crear pruebas de carga para ayudar a aislar los problemas de rendimiento y esfuerzo de la aplicación (en desuso).|- [Inicio rápido: Creación de un proyecto de prueba de carga](../test/quickstart-create-a-load-test-project.md)<br />- [Prueba de carga (Azure Test Plans y TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Establecimiento de puertas de calidad:** Descubra cómo puede crear puertas de calidad para exigir que las pruebas se ejecuten antes de insertar el código en el repositorio o combinarlo.|- [Directivas de inserción en el repositorio (Azure Repos y TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Establecimiento de opciones de prueba:** Obtenga información sobre la configuración de las opciones de prueba (por ejemplo, dónde se almacenan los resultados de las pruebas).|[Configurar pruebas unitarias mediante un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentación de referencia de API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> describe el espacio de nombres UnitTesting, que proporciona los atributos, excepciones, aserciones y otras clases que ofrecen compatibilidad para prueba unitaria.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> describe el espacio de nombres UnitTesting.Web, que extiende el espacio de nombres UnitTesting proporcionando compatibilidad para ASP.NET y pruebas unitarias de servicios web.

## <a name="see-also"></a>Consulte también

- [Mejorar la calidad del código](../test/improve-code-quality.md)