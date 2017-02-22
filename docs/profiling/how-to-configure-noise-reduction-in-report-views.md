---
title: "C&#243;mo: Configurar la reducci&#243;n de ruido en las vistas de informes de las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, recortes"
  - "herramientas de generación de perfiles, reducción de ruido de informes"
  - "herramientas de generación de perfiles, plegamiento"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Configurar la reducci&#243;n de ruido en las vistas de informes de las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los informes de rendimiento se pueden configurar para la reducción de ruido limitando la cantidad de datos que se presentan en las vistas Árbol de llamadas y Asignación.  Al utilizar la reducción de ruido, los problemas de rendimiento destacan más.  Esto le servirá de ayuda al analizar los informes de rendimiento.  
  
 Las opciones de configuración de la reducción de ruido incluyen las siguientes:  
  
-   **Reducción**: cuando se analiza un informe, la vista omite las funciones comprendidas en la configuración de valores y de umbral que haya establecido, tal como se describe en el procedimiento de reducción que figura a continuación.  La opción de reducción está habilitada de forma predeterminada.  
  
-   **Plegamiento**: si habilita el plegamiento, las funciones consecutivas en una ruta de acceso que cumplan los valores que haya configurado se combinarán como se describe en el procedimiento de plegamiento que figura a continuación.  De forma predeterminada, el plegamiento está habilitado.  
  
### Para configurar la reducción de un informe de rendimiento  
  
1.  Con la vista Árbol de llamadas o Asignación abierta en el informe generado, en el menú **Desarrollador**, haga clic en **Generador de perfiles** y, a continuación, haga clic en **Opciones de reducción de ruido**.  
  
     Aparece el cuadro de diálogo **Reducción de ruido**.  
  
2.  Para habilitar reducción, siga estos pasos:  
  
    1.  Seleccione **Habilitar reducción**.  Ésta es la configuración predeterminada.  
  
        > [!NOTE]
        >  Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe.  Para obtener más información, vea [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Para configurar el valor, utilice la lista desplegable **Valor** y elija el valor aplicable.  
  
    3.  Para configurar el valor de umbral deseado, escriba un valor de porcentaje en el cuadro de texto **Umbral**.  
  
    4.  Para habilitar la advertencia de reducción de ruido en el informe generado, seleccione **Mostrar advertencia cuando la reducción de ruido está habilitada**.  Ésta es la configuración predeterminada.  
  
3.  Para deshabilitar la reducción, desactive **Habilitar reducción**.  
  
4.  Haga clic en **Aceptar**.  
  
### Para configurar el plegamiento de un informe de rendimiento  
  
1.  En el menú **Desarrollador**, haga clic en **Generador de perfiles** y, a continuación, haga clic en **Opciones de reducción de ruido**.  
  
     Aparece el cuadro de diálogo **Reducción de ruido**.  
  
2.  Para habilitar el plegamiento, siga estos pasos:  
  
    1.  Seleccione **Habilitar plegamiento**.  Ésta es la configuración predeterminada.  
  
        > [!NOTE]
        >  Si está habilitada la reducción de ruido, se mostrará una barra de información en el informe.  Para obtener más información, vea [Vista Árbol de llamadas](../profiling/call-tree-view.md) y [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Para configurar el valor, utilice la lista desplegable **Valor** y elija el valor aplicable.  
  
    3.  Para configurar el valor de umbral deseado, escriba un valor de porcentaje en el cuadro de texto **Umbral**.  
  
    4.  Para habilitar la advertencia de reducción de ruido en el informe generado, seleccione **Mostrar advertencia cuando la reducción de ruido está habilitada**.  Ésta es la configuración predeterminada.  
  
3.  Para deshabilitar el doblado, desactive **Habilitar plegamiento**.  
  
4.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Personalizar las vistas de los informes de las Herramientas de generación de perfiles](../profiling/customizing-performance-tools-report-views.md)   
 [Cómo: Excluir o incluir funciones cortas en la instrumentación](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view.md)   
 [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md)