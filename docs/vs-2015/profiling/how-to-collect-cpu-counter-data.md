---
title: 'Cómo: Recopilar datos de contadores de CPU | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f7c9f88dbbc3d7d2022736528f2b35fa3a325b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47583177"
---
# <a name="how-to-collect-cpu-counter-data"></a>Cómo: Recopilar datos de contadores de CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: recopilar datos de contadores de CPU](https://docs.microsoft.com/visualstudio/profiling/how-to-collect-cpu-counter-data).  
  
Un contador de eventos de CPU se utiliza para recopilar datos de rendimiento específicos de hardware. En este tema se muestra cómo recopilar datos de contador de eventos cuando se utiliza el método de generación de perfiles de instrumentación.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Se producen dos tipos de eventos de contador de CPU:  
  
-   Eventos portátiles: eventos de CPU que se pueden recopilar independientemente de una CPU concreta.  
  
-   Eventos de plataforma: eventos de CPU que están asociados a una CPU específica.  
  
 Los eventos portátiles incluyen eventos generales, como instrucciones retiradas y ciclos no detenidos, eventos de búfer de la CPU, eventos de bifurcación y eventos de caché L2. El fabricante del procesador determina los contadores de eventos de plataforma disponibles.  
  
 Las categorías de eventos pueden compartirse entre los contadores de eventos portátiles y de plataforma. Por ejemplo, las siguientes categorías de datos son con frecuencia comunes a ambos tipos:  
  
-   Eventos de memoria.  
  
-   Eventos de front-end.  
  
-   Eventos de bifurcación.  
  
 Puede recopilar datos del contador de rendimiento de dos formas en el generador de perfiles:  
  
-   Recopilar datos de uno o más contadores al generar perfiles mediante la instrumentación.  
  
-   Especificar un evento de contador como el intervalo de muestreo al generar perfiles mediante el muestreo. Para obtener más información, consulte [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md).  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Para recopilar datos del contador de rendimiento de CPU al generar perfiles mediante la instrumentación  
  
1.  En las **Páginas de propiedades** de la sesión de rendimiento, haga clic en **Contadores de CPU**.  
  
2.  Seleccione la casilla **Recopilar contadores de CPU**.  
  
3.  Expanda el árbol **Contadores de rendimiento disponibles** hasta que encuentre los eventos de ejemplo que se van a recopilar.  
  
4.  Para cada evento que se va a recopilar, seleccione el evento y, a continuación, haga clic en la flecha derecha para agregar el evento a la lista **Contadores seleccionados**.  
  
    > [!NOTE]
    >  **Contadores de rendimiento disponibles** está habilitado solo si selecciona la casilla **Recopilar contadores de CPU**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)   
 [Contadores de CPU y de Windows](../profiling/cpu-and-windows-counters.md)   
 [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md)



