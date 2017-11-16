---
title: "Descripción de los valores de datos de contención de recursos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4e128fa9a557569eb737a2b0a70ce60687d0830
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="understanding-resource-contention-data-values"></a>Descripción de los valores de datos de contención de recursos
La generación de perfiles de contención de recursos recopila información detallada de la pila de llamadas cada vez que subprocesos competidores en una aplicación se ven obligados a esperar para obtener acceso a un recurso compartido.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Los informes de contención de recursos muestran el número total de contenciones y el tiempo total invertido esperando a un recurso por los módulos, funciones, líneas del código fuente e instrucciones en los que se produjo la espera.  
  
-   Los valores inclusivos muestran el número total de contenciones que obligan a una función a esperar por las contenciones de recursos y el tiempo total de espera de la función.  Las contenciones originadas por funciones secundarias llamadas por la función se incluyen en los valores inclusivos.  
  
-   Los valores exclusivos muestran solo el número de contenciones que obligan a una función a esperar y que están causadas por el código en el cuerpo de la función. No se incluyen las contenciones producidas por funciones secundarias. El tiempo exclusivo de la función también incluye los tiempos de espera producidos por instrucciones del cuerpo de la función.  
  
 Las vistas de informes de contención de recursos también incluyen gráficos de escala de tiempo que se muestran los eventos de contención individuales a lo largo del tiempo y muestran las pilas de llamadas que crearon el evento concreto. Para obtener más información, consulte uno de los temas siguientes:  
  
-   [Vista Detalles del subproceso](../profiling/thread-details-view-contention-data.md)  
  
-   [Vista Detalles de recursos](../profiling/resource-details-view-contention-data.md)  
  
 Para obtener más información sobre el segundo modo de generación de perfiles de simultaneidad, consulte [visualizador de simultaneidad](../profiling/concurrency-visualizer.md).