---
title: Procedimiento Configurar la reducción de ruido en las vistas de informes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6974d7606a6c60df785fe2301a695f6775716d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106090"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Procedimiento Configurar la reducción de ruido en las vistas de informes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
        >  Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe. Para obtener más información, consulte [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md).  
  
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
        >  Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe. Para obtener más información, consulte [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Configure el valor con la lista desplegable **Valor**; seleccione el valor aplicable.  
  
    3. Configure el valor de umbral deseado escribiendo un valor de porcentaje en el cuadro de texto **Umbral**.  
  
    4. Para habilitar la advertencia de reducción de ruido en el informe generado, seleccione **Mostrar advertencia cuando se habilita la reducción de ruido**. Ésta es la configuración predeterminada.  
  
3. Para deshabilitar el plegado, desactive **Habilitar plegado**.  
  
4. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar las vistas de Informes de las Herramientas de rendimiento](../profiling/customizing-performance-tools-report-views.md)   
 [Cómo: Excluir o incluir funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view.md)   
 [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md)
