---
title: "Introducción a los valores de datos de muestreo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95869fd4c3b52853417c847d32f7507c90471c2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sampling-data-values"></a>Introducción a los valores de datos de muestreo
El método de generación de perfiles de *muestreo* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interrumpe el procesador del equipo a intervalos establecidos y recopila la pila de llamadas a función. Una *pila de llamadas* es una estructura dinámica que almacena información sobre las funciones que se ejecutan en el procesador.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 El análisis del generador de perfiles determina si el procesador está ejecutando código en el proceso de destino. Si el procesador no está ejecutando código en el proceso de destino, se descarta la muestra.  
  
 Si el procesador está ejecutando código en el proceso de destino, el generador de perfiles incrementa los recuentos de muestras para cada función en la pila de llamadas. En el momento en que se tomó la muestra, solo una función en la pila de llamadas está ejecutando el código. Las demás funciones de la pila son elementos primarios en la jerarquía de llamadas de función que están esperando a que las secundarias devuelvan información.  
  
 Para el evento de muestreo, el generador de perfiles incrementa la muestra *exclusiva* del recuento de la función que está ejecutando actualmente sus instrucciones. Dado que una muestra exclusiva también forma parte de las muestras totales (*inclusivas*) de la función, también se incrementa el recuento de muestras inclusivas de la función actualmente activa.  
  
 El generador de perfiles incrementa el recuento de muestras inclusivas de todas las demás funciones en la pila de llamadas.  
  
## <a name="inclusive-samples"></a>Muestras inclusivas  
 El número total de muestras recopiladas durante la ejecución de la función de destino.  
  
 Esto incluye muestras recopiladas durante la ejecución directa del código de función y las muestras recopiladas durante la ejecución de las funciones secundarias llamadas por la función de destino.  
  
## <a name="exclusive-samples"></a>Muestras exclusivas  
 El número de muestras recopiladas durante la ejecución directa de las instrucciones de la función de destino.  
  
 Entre las muestras exclusivas no se incluyen las muestras recopiladas durante la ejecución de funciones a las que llama la función de destino.  
  
## <a name="inclusive-percent"></a>Porcentaje de inclusivas  
 El porcentaje del número total de muestras inclusivas de la generación de perfiles que son muestras inclusivas de la función o el rango de datos.  
  
## <a name="exclusive-percent"></a>Porcentaje de exclusivas  
 El porcentaje del número total de muestras exclusivas de la generación de perfiles que son muestras exclusivas de la función o el rango de datos.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Elegir métodos de recopilación](../profiling/how-to-choose-collection-methods.md)   
 [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)