---
title: "C&#243;mo: Recopilar datos de los contadores de CPU mediante el m&#233;todo de instrumentaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, uso de contadores de CPU portátiles"
  - "herramientas de rendimiento, uso de contadores de CPU portátiles"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Recopilar datos de los contadores de CPU mediante el m&#233;todo de instrumentaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un contador de eventos de CPU se utiliza para recopilar los datos de rendimiento específicos del hardware.  Este tema muestra cómo conseguir datos de recuento de eventos cuando se utiliza el método de perfiles de instrumentación.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Se producen dos tipos de eventos de contador de CPU:  
  
-   Eventos portátiles: eventos de CPU que se pueden recopilar independientemente de la CPU concreta.  
  
-   Eventos de la plataforma: eventos de CPU que se acoplan a una CPU concreta.  
  
 Entre los eventos portátiles se incluyen eventos generales, como Instrucciones retiradas y Ciclos no detenidos; eventos del búfer de la CPU; eventos de bifurcación, y eventos de caché en L2.  Los contadores disponibles de eventos de la plataforma vienen determinados por el fabricante del procesador.  
  
 Las categorías de eventos pueden compartirse entre los contadores móviles y de la plataforma.  Por ejemplo, las siguientes categorías de datos suelen ser comunes a ambos tipos:  
  
-   Eventos de memoria.  
  
-   Eventos de front\-end.  
  
-   Eventos de bifurcaciones.  
  
 En el generador de perfiles, puede recopilar datos de contadores de rendimiento de dos formas:  
  
-   Recopile datos de uno o más contadores al generar perfiles por instrumentación.  
  
-   Especifique un evento de contador como intervalo de muestreo al generar perfiles por muestreo.  Para obtener más información, vea [Cómo: Elegir eventos de muestreo](../Topic/How%20to:%20Choose%20Sampling%20Events.md).  
  
### Para recopilar datos de contadores de rendimiento de CPU al generar perfiles por instrumentación  
  
1.  En las **Páginas de propiedades** de la sesión de rendimiento, haga clic en **Contadores de CPU**.  
  
2.  Active la casilla **Recopilar contadores de CPU**.  
  
3.  Expanda el árbol **Contadores de rendimiento disponibles** hasta que encuentre los eventos de muestreo que desea recopilar.  
  
4.  Por cada evento que desee recopilar, seleccione el evento y haga clic en la flecha derecha para agregarlo a la lista **Contadores seleccionados**.  
  
    > [!NOTE]
    >  La opción **Contadores de rendimiento disponibles** solamente está habilitada si activa la casilla **Recopilar contadores de CPU**.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)   
 [Contadores de Windows y de CPU](../profiling/cpu-and-windows-counters.md)   
 [Cómo: Elegir eventos de muestreo](../Topic/How%20to:%20Choose%20Sampling%20Events.md)