---
title: Vista de utilización | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 238d821795aaa4e9ef0ac06e117316450b46fda4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795837"
---
# <a name="utilization-view"></a>Vista de utilización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La **Vista de utilización** muestra información acerca de la CPU, la GPU y otros recursos del sistema utilizados por el proceso actual. Muestra el uso de núcleo promedio por el proceso analizado, el proceso inactivo, el proceso del sistema y otros procesos que se ejecutan en el sistema a lo largo del tiempo. No muestra qué núcleo concreto está activo en un momento dado. Por ejemplo, si dos núcleos se ejecutan al 50 por ciento de su capacidad durante un período de tiempo determinado, esta vista muestra que se está utilizando un núcleo lógico. La vista se genera al dividir el tiempo de generación de perfiles en segmentos de tiempo cortos. Para cada segmento, el gráfico traza el promedio de subprocesos del proceso que se ejecutan en núcleos lógicos durante ese intervalo.  
  
 ![Vista de utilización de CPU](../profiling/media/vsts-ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 El gráfico muestra el tiempo (en el eje x) y el promedio de núcleos lógicos que se utilizan en el proceso de destino, el proceso inactivo y el proceso del sistema. (El proceso inactivo muestra núcleos inactivos. El proceso del sistema es un proceso de Windows que puede realizar trabajo en nombre de otros procesos). Los procesos restantes que se ejecutan en el sistema utilizan los núcleos restantes.  
  
 El número de núcleos lógicos se muestra en el eje y. Windows trata la compatibilidad con multithreading simultáneo en el hardware como núcleos lógicos (por ejemplo, Hyper-Threading). Por lo tanto, un sistema que tiene un procesador de cuatro núcleos que admite dos subprocesos de hardware por núcleo aparecerá como un sistema de ocho núcleos lógicos. Esto también se aplica a la vista Núcleos. Para obtener más información, consulte [Vista Núcleos](../profiling/cores-view.md).  
  
 El diagrama de actividad de GPU, muestra el número de motores de DirectX en uso a lo largo del tiempo.  Un motor está en uso si se está procesando un paquete DMA.  El gráfico no muestra el motor de DirectX específico (por ejemplo, 3D Engine, Video Engine y los demás).  
  
## <a name="purpose"></a>Propósito  
 Se recomienda la vista de utilización como punto de partida de las investigaciones de rendimiento al usar el visualizador de simultaneidad. Dado que proporciona una visión general del grado de simultaneidad en una aplicación a lo largo del tiempo, puede utilizarla para identificar rápidamente las áreas que requieren que se optimice el rendimiento o el uso de la ejecución en paralelo.  
  
 Si le interesa la optimización del rendimiento, es posible que intente identificar comportamiento que no cumple las expectativas. También podría estar buscando la existencia y la causa de las regiones con poca utilización de núcleos de CPU lógicos. Puede que también esté buscando patrones de uso entre la CPU y la GPU.  
  
 Si le interesa paralelizar una aplicación, probablemente busca áreas de ejecución enlazadas a la CPU o áreas donde no se está utilizando la CPU.  
  
 Las áreas enlazadas a la CPU son verdes. El gráfico muestra un núcleo que se utiliza si la aplicación es en serie.  
  
 Las áreas donde no se está utilizando la CPU aparecen en gris. Éstas podrían representar puntos en los que la aplicación está inactiva o realizando E/S de bloqueo que proporciona oportunidades para el paralelismo mediante la superposición con otro trabajo enlazado a la CPU.  
  
 Cuando encuentre un comportamiento interesante, puede ampliar región en la que está seleccionándola. Después de ampliar, puede cambiar a la vista de subprocesos o la vista Núcleos para un análisis más detallado.  
  
 Si utiliza la GPU mediante C++ AMP o DirectX, quizá le interese identificar el número de motores de GPU en uso o de áreas donde la GPU está inactiva de forma inesperada.  
  
## <a name="zooming"></a>Zoom  
 Para ampliar el gráfico de utilización de CPU o el gráfico de actividad de GPU, seleccione una sección o utilice el control deslizante de zoom sobre el gráfico. La configuración de zoom se conserva cuando se cambia a otras vistas. Para reducir, use el control deslizante de zoom. También puede hacer zoom presionando Ctrl + rueda del mouse.  
  
## <a name="see-also"></a>Vea también  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)   
 [Vista Núcleos](../profiling/cores-view.md)
