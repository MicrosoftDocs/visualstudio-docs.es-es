---
title: "Introducci&#243;n a los valores de datos de contenci&#243;n de recursos en las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de simultaneidad"
  - "Herramientas de generación de perfiles, método de simultaneidad"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introducci&#243;n a los valores de datos de contenci&#243;n de recursos en las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El perfil de contención de recursos recopila información detallada sobre la pila de llamadas cada vez que los subprocesos competidores de una aplicación se ven forzados a esperar para obtener acceso a un recurso compartido.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 En los informes de contención de recursos se muestra el número total de contenciones y el tiempo total invertido a la espera de un recurso de los módulos, funciones, líneas del código fuente e instrucciones en los que se produjo la espera.  
  
-   Los valores inclusivos muestran el número total de contenciones que obligan a una función a esperar por las contenciones de recursos y el tiempo total de espera de la función.  Las contenciones originadas por funciones secundarias invocadas por la función se incluyen en los valores inclusivos.  
  
-   Los valores exclusivos muestran únicamente el número de contenciones que obligan a una función a esperar y que están causadas por el código del cuerpo de la función.  Las contenciones producidas por funciones secundarias no se incluyen.  El tiempo exclusivo de la función también incluye únicamente los tiempos de espera producidos por instrucciones del cuerpo de la función.  
  
 Las vistas de informes de contención de recursos también incluyen gráficos de escala de tiempo en los que se muestra cada uno de los eventos de contención en el tiempo y las pilas de llamadas que crearon el evento concreto.  Para obtener más información, consulte uno de los temas siguientes:  
  
-   [Detalles del subproceso \(vista\)](../profiling/thread-details-view-contention-data.md)  
  
-   [Detalles de recursos \(Vista\)](../profiling/resource-details-view-contention-data.md)  
  
 Para obtener más información sobre el segundo modo de generación de perfiles de simultaneidad, vea [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md).