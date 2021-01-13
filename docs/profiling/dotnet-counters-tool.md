---
title: Visualización de los contadores de dotnet | Microsoft Docs
description: Aprenda a usar la herramienta .NET Counters en el Generador de perfiles de rendimiento de Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905090"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualización de los contadores de dotnet desde el generador de perfiles de Visual Studio


La herramienta .NET Counters le permite visualizar los [contadores de dotnet](/dotnet/core/diagnostics/dotnet-counters) a lo largo del tiempo directamente desde el generador de perfiles de Visual Studio.


> [!NOTE]
> La herramienta .NET Counters requiere Visual Studio 2019 versión 16.7 o superior, y tiene como destino .NET Core 3.0 y versiones posteriores.

## <a name="setup"></a>Configurar

1. Abra el Generador de perfiles de rendimiento (**Alt+F2** o **Depurar -> Generador de perfiles de rendimiento**) en Visual Studio.

2. Seleccione la casilla **.NET Counters**.

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Herramienta de contadores seleccionada.":::

3. Haga clic en el botón **Iniciar** para ejecutar la herramienta.

Para obtener más información sobre cómo optimizar el rendimiento de la herramienta, consulte el artículo [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Comprensión de los datos

Mientras la herramienta recopila datos inicialmente, puede ver los valores activos de los [contadores de dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Herramienta .NET Counters recopilando datos.":::

También puede ver gráficos de los contadores activando la casilla situada junto a sus nombres. Puede mostrar gráficos de varios contadores a la vez.


Cuando haya terminado de ejecutar la aplicación y de recopilar datos, puede detener la recopilación para obtener un informe más detallado. Para ello, presione el botón **Detener recolección**.


Una vez cargado, el informe completo debería tener un aspecto similar al que se muestra a continuación.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Informe de la herramienta .NET Counters.":::

El informe muestra los valores siguientes:

- Mín.: el valor mínimo de ese contador en el intervalo de tiempo seleccionado.
- Max.: el valor máximo de ese contador en el intervalo de tiempo seleccionado.
- Promedio: el valor medio de ese contador en el intervalo de tiempo seleccionado.

Puede filtrar o agregar columnas en la tabla haciendo clic con el botón derecho en los encabezados de columna y seleccionando uno.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Columnas de la herramienta .NET Counters.":::

También puede ver los gráficos en el informe detallado activando las casillas junto a los contadores. De forma predeterminada, los datos de las tablas representan los valores de la duración completa del seguimiento recopilado. Para filtrar los datos y mostrar un intervalo de tiempo concreto, haga clic en los gráficos y arrástrelos.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtrado de tiempo de la herramienta .NET Counters.":::

La tabla se actualiza con los valores relevantes para el período de tiempo seleccionado en los gráficos. Use el botón **Borrar selección** para restablecer el intervalo de tiempo seleccionado en todo el seguimiento.


## <a name="see-also"></a>Vea también

- [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md)
- [Contadores de dotnet](/dotnet/core/diagnostics/dotnet-counters)
