---
title: Depuración de pruebas unitarias con el Explorador de pruebas
description: Obtenga información sobre cómo depurar pruebas unitarias con el Explorador de pruebas en Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09889839c9e2873810c78a5f0c3425820170b68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964386"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Depuración y análisis de pruebas unitarias con el Explorador de pruebas

Se puede usar el Explorador de pruebas para iniciar una sesión de depuración para las pruebas. La ejecución paso a paso del código con el depurador de Visual Studio permite avanzar y retroceder sin problemas entre las pruebas unitarias y el proyecto objeto de prueba. Para iniciar la depuración:

1. En el editor de Visual Studio, establezca un punto de interrupción en uno o varios métodos de prueba que desee depurar.

    > [!NOTE]
    > Dado que los métodos de prueba se pueden ejecutar en cualquier orden, establezca puntos de interrupción en todos los métodos de prueba que desee depurar.

::: moniker range="vs-2017"
2. En el Explorador de pruebas, seleccione los métodos de prueba que quiera y elija **Depurar pruebas seleccionadas** en el menú contextual.
::: moniker-end
::: moniker range=">=vs-2019"
2. En el Explorador de pruebas, seleccione los métodos de prueba que quiera y seleccione **Depurar** en el menú contextual.

   ![Detalles de ejecución de las pruebas](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Para obtener más información sobre el depurador, vea [Depurar en Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnosticar problemas de rendimiento del método de prueba

::: moniker range="vs-2017"
Para diagnosticar por qué tarda demasiado un método de prueba, selecciónelo en el Explorador de pruebas y, luego, elija **Profile Selected Test** (Prueba seleccionada de perfil) en el menú contextual. Vea [Informe de generación de perfiles de instrumentación](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

::: moniker range=">=vs-2019"
Para diagnosticar por qué tarda demasiado un método de prueba, seleccione el método en el Explorador de pruebas y, en el menú contextual, haga clic en **Perfil**. Vea [Informe de generación de perfiles de instrumentación](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

> [!NOTE]
> Esta característica no se admite actualmente en .NET Core.

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)
- [Preguntas más frecuentes sobre el Explorador de pruebas](test-explorer-faq.md)
