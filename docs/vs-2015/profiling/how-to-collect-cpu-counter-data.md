---
title: 'Cómo: Recopilar datos de contadores de CPU | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a774ce8b36ceddb4d4b53f90c63bec30acc0273
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762937"
---
# <a name="how-to-collect-cpu-counter-data"></a>Cómo: Recopilar datos de contadores de CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un contador de eventos de CPU se utiliza para recopilar datos de rendimiento específicos de hardware. En este tema se muestra cómo recopilar datos de contador de eventos cuando se utiliza el método de generación de perfiles de instrumentación.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Se producen dos tipos de eventos de contador de CPU:  
  
- Eventos portátiles: eventos de CPU que se pueden recopilar independientemente de una CPU concreta.  
  
- Eventos de plataforma: eventos de CPU que están asociados a una CPU específica.  
  
  Los eventos portátiles incluyen eventos generales, como instrucciones retiradas y ciclos no detenidos, eventos de búfer de la CPU, eventos de bifurcación y eventos de caché L2. El fabricante del procesador determina los contadores de eventos de plataforma disponibles.  
  
  Las categorías de eventos pueden compartirse entre los contadores de eventos portátiles y de plataforma. Por ejemplo, las siguientes categorías de datos son con frecuencia comunes a ambos tipos:  
  
- Eventos de memoria.  
  
- Eventos de front-end.  
  
- Eventos de bifurcación.  
  
  Puede recopilar datos del contador de rendimiento de dos formas en el generador de perfiles:  
  
- Recopilar datos de uno o más contadores al generar perfiles mediante la instrumentación.  
  
- Especificar un evento de contador como el intervalo de muestreo al generar perfiles mediante el muestreo. Para obtener más información, consulte [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md).  
  
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
