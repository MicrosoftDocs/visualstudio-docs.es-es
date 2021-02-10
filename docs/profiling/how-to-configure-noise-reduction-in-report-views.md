---
title: Configurar la reducción de ruido en las vistas de informes | Microsoft Docs
description: Use los procedimientos de recorte y plegado, ambos habilitados de forma predeterminada, para reducir el ruido y destacar más los problemas de rendimiento en los informes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5037cf0184608829d5a86d736bead5b61f5172c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969339"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Procedimiento Configurar la reducción de ruido en las vistas de informes
Los informes de rendimiento pueden configurarse para la reducción de ruido limitando la cantidad de datos que se presentan en la vistas Árbol de llamadas y Asignación. Gracias a la reducción de ruido, los problemas de rendimiento destacan más. Esto es útil a la hora de analizar informes de rendimiento.

 Las opciones de configuración de reducción de ruido incluyen:

- **Recorte** Cuando se analice un informe, la vista omitirá las funciones que se encuentran en la configuración de valor y umbral que ha establecido, como se describe en el siguiente procedimiento de recorte. De forma predeterminada, Recorte está habilitado.

- **Plegado** Si habilita el plegado, se combinarán las funciones consecutivas en una ruta de acceso que cumplen la configuración que ha establecido, como se describe en el siguiente procedimiento de plegado. De forma predeterminada, el plegado está habilitado.

### <a name="to-configure-trimming-for-a-performance-report"></a>Para configurar el recorte de un informe de rendimiento

1. Cuando una vista Árbol de llamadas o Asignación se muestra en el informe generado, en el menú **Desarrollador** haga clic en **Generador de perfiles** y después en **Opciones de reducción de ruido**.

     Aparece el cuadro de diálogo **Reducción de ruido**.

2. Para habilitar el recorte debe seguir estos pasos:

    1. Seleccione **Habilitar recorte**. Ésta es la configuración predeterminada.

        > [!NOTE]
        > Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe. Para obtener más información, consulte [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md).

    2. Configure el valor con la lista desplegable **Valor**; elija el valor aplicable.

    3. Configure el valor de umbral deseado escribiendo un valor de porcentaje en el cuadro de texto **Umbral**.

    4. Para habilitar la advertencia de reducción de ruido en el informe generado, seleccione **Mostrar advertencia cuando se habilita la reducción de ruido**. Ésta es la configuración predeterminada.

3. Para deshabilitar el recorte, desactive **Habilitar recorte**.

4. Haga clic en **Aceptar**.

### <a name="to-configure-folding-for-a-performance-report"></a>Para configurar el plegado de un informe de rendimiento

1. En el menú **Desarrollador**, haga clic en **Generador de perfiles** y después en **Opciones de reducción de ruido**.

     Aparece el cuadro de diálogo **Reducción de ruido**.

2. Para habilitar el plegado debe seguir estos pasos:

    1. Seleccione **Habilitar plegamiento**. Ésta es la configuración predeterminada.

        > [!NOTE]
        > Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe. Para obtener más información, consulte [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md).

    2. Configure el valor con la lista desplegable **Valor**; seleccione el valor aplicable.

    3. Configure el valor de umbral deseado escribiendo un valor de porcentaje en el cuadro de texto **Umbral**.

    4. Para habilitar la advertencia de reducción de ruido en el informe generado, seleccione **Mostrar advertencia cuando se habilita la reducción de ruido**. Ésta es la configuración predeterminada.

3. Para deshabilitar el plegado, desactive **Habilitar plegado**.

4. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
- [Personalizar las vistas de informes de las herramientas de rendimiento](../profiling/customizing-performance-tools-report-views.md)
- [Cómo: Excluir o incluir funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Vista Árbol de llamadas](../profiling/call-tree-view.md)
- [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md)
