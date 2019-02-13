---
title: Modificar pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 130f7296985aa5c5e6115cd3e61b00efd90f25c7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934450"
---
# <a name="edit-load-tests"></a>Editar pruebas de carga

Las pruebas de carga ejecutan pruebas unitarias o de rendimiento web para simular que muchos usuarios acceden a un servidor al mismo tiempo. Una prueba de carga permite tener acceso a los datos de rendimiento y esfuerzo de una aplicación. Estas pruebas se pueden configurar para emular varias condiciones de carga, como cargas de usuario y tipos de red.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Una prueba de carga se define mediante *escenarios*, *conjuntos de contadores* y *parámetros de ejecución*. En la ilustración siguiente se explican las diferencias entre [escenarios](../test/edit-load-test-scenarios.md), [conjuntos de contadores](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) y [parámetros de ejecución](../test/load-test-run-settings-properties.md):

![Arquitectura de Prueba de carga](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Requisitos de software

Los proyectos de prueba de carga y rendimiento web solo están disponibles en la edición Enterprise de Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Editar la configuración del escenario de prueba de carga

Un escenario se usa para modelar cómo interactúa un grupo de usuarios con una aplicación de servidor. Un escenario consta de un modelo de carga, un modelo de combinación de pruebas, una combinación de pruebas, una combinación de exploradores y una combinación de redes. Una prueba de carga puede tener más de un escenario y un escenario único puede contener pruebas de rendimiento web y pruebas unitarias. Agrupando opciones de configuración similares, un escenario permite agrupar y ejecutar conjuntamente pruebas de naturaleza similar.

Para más información, consulte [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md) y [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Configurar y administrar conjuntos de contadores de rendimiento

Las pruebas de carga proporcionan conjuntos de contadores con nombre, organizados por tecnología, que son útiles cuando se analizan datos del contador de rendimiento. Entre los conjuntos de contadores se incluyen Prueba de carga, IIS, ASP.NET y SQL. Cuando se crea una prueba de carga con el **Asistente para prueba de carga nueva**, se configura un conjunto inicial de contadores predefinidos e importantes para los equipos que especifique que se incluyan en la prueba de carga. Los contadores se administran en el **Editor de pruebas de carga**.

Para más información, consulte [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Configurar y administrar parámetros de ejecución de pruebas de carga

Los parámetros de ejecución son propiedades que influyen en la manera en que se ejecuta una prueba de carga. Los parámetros de ejecución están organizados por categorías en la ventana **Propiedades**.

Para más información, consulte [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md) y [Propiedades de los parámetros de ejecución de pruebas de carga](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)