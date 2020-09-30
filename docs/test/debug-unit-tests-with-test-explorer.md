---
title: Depuración de pruebas unitarias con el Explorador de pruebas
description: Obtenga información sobre cómo depurar pruebas unitarias con el Explorador de pruebas en Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b811cc3538e3bbb108e50acf50c2fe7a977fe3d
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211292"
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
