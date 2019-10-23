---
title: Creación de un informe de rendimiento de la prueba de carga con Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 715086a2c0d9196680dd1f332ee9b5122e144e5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653478"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Procedimiento para crear manualmente un informe de rendimiento de pruebas de carga con Microsoft Word

Puede crear manualmente informes de prueba de carga en Microsoft Word copiando y pegando los datos de la vista de resumen de resultados de pruebas de carga y de la vista de gráficos. Los datos que se presentan en la vista de resumen y de gráficos se aplican en formato HTML cuando se copian.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> También puede copiar el texto sin formato de la vista de tablas y las capturas de pantalla de la vista de detalles de Microsoft Word, pero no se aplica en formato HTML, por lo que precisará formato y edición adicionales.

> [!TIP]
> También puede generar informes organizados de Microsoft Excel automáticamente. Para obtener más información, vea [Cómo: Crear informes de rendimiento de pruebas de carga con Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Copiar datos de la vista Resumen

1. En **Resultados de pruebas de carga**, si no se muestra la vista de resumen, haga clic en **Resumen** en la barra de herramientas.

2. En la vista de resumen, haga clic con el botón derecho y seleccione **Seleccionar todo**.

3. En la vista de resumen, haga clic con el botón derecho y seleccione **Copiar**. Esto presenta los datos de la vista de resumen en formato HTML en el portapapeles.

4. En Microsoft Word, pegue los datos de la vista de resumen en la ubicación deseada.

5. Ahora puede modificar, dar formato y eliminar aspectos del contenido copiado para satisfacer las necesidades del informe de errores.

## <a name="copy-graph-view-data"></a>Copiar datos de la vista del gráfico

1. En **Resultados de pruebas de carga**, si no se muestra la vista de gráfico, elija **Gráficos** en la barra de herramientas.

2. (Opcional) Haga zoom en el gráfico concreto que desea copiar en el documento de Microsoft Word, como se muestra en la siguiente ilustración. Para obtener más información, vea [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Control de zoom de la vista de gráficos](../test/media/ltest_zoomcontrol.png)

3. En el gráfico que desea copiar en el documento de Microsoft Word, haga clic con el botón derecho y seleccione **Copiar**.

4. En Microsoft Word, pegue el gráfico y los datos de la tabla asociados en la ubicación deseada.

    > [!WARNING]
    > No puede copiar el gráfico de un escritorio remoto y pegarlo en otro equipo, porque se copiará solo la información de la tabla asociada al gráfico y no la imagen del gráfico. La imagen del gráfico está almacenada en el directorio temporal de la máquina de la que se copió; la segunda máquina no puede desreferenciar ese directorio.

## <a name="see-also"></a>Vea también

- [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md)
- [Cómo: Crear informes de rendimiento de pruebas de carga con Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)