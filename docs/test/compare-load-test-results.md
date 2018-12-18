---
title: Comparación de los resultados de pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fc54324f2c5bc91dba64aa35b125bbdc12ca1a45
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895033"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias

Puede generar informes de prueba de carga de Microsoft Excel basados en dos o más resultados de pruebas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Están disponibles dos informes de prueba de carga:

- Ejecutar comparación&mdash;Este informe consta realmente de dos informes que muestran datos de comparación en paralelo mediante tablas y gráficos de barras.

- Tendencia: puede generar análisis de tendencias en dos o más informes. Los resultados se muestran mediante gráficos de líneas.

Se puede usar cualquier de estos dos informes para compartir los datos de rendimiento con las partes interesadas y mostrar si el rendimiento global y el estado del sistema mejoran o empeoran.

Las definiciones de informe están almacenadas en la base de datos de pruebas de carga. Cuando se guarda un informe, su definición se guarda en la base de datos y se puede volver a usar más adelante.

Además, el archivo de hoja de cálculo se puede compartir con las partes interesadas de forma que no tengan que conectarse a la base de datos para ver el informe.

> [!NOTE]
> Si agrega comentarios a una prueba de carga, aparecen en el informe de Excel.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-|
|**Crear un informe de rendimiento y esfuerzo:** puede crear informes en las pruebas de rendimiento web y carga, utilizando Microsoft Excel.|- [Cómo: Crear informes de rendimiento de la prueba de carga con Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Crear manualmente un informe de rendimiento y tensión con Microsoft Word:** para crear informes de las pruebas de carga y rendimiento web, copie y pegue el resumen, la tabla y los datos del gráfico en un documento de Microsoft Word.|- [Cómo: Crear manualmente informes de rendimiento de pruebas de carga con Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)