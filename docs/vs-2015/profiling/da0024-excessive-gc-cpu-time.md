---
title: 'DA0024: Tiempo excesivo de CPU de GC | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910f66a31f959fe15cc7165eda4e531e7965e670
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754256"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Tiempo excesivo de CPU de GC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0024 |  
| Categoría |. Uso de .NET Framework |  
| Método de generación de perfiles | Todos los |  
| Mensaje | % de tiempo del GC es muy alta. Hay una cantidad excesiva de recolección. |  
| Tipo de regla | Advertencia |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es excesivamente alta en comparación con el tiempo total de procesamiento de la aplicación.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Run-time (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que utiliza un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no utiliza. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de una manera muy eficaz. Los objetos de la generación 1 se recopilan con menos frecuencia y, normalmente, de una manera menos eficaz. Por último, los objetos de larga duración de la generación 2 se deben recopilar incluso con menos frecuencia. La colección de la generación 2, que es una ejecución de recolección de elementos no utilizados completa, es también la operación más costosa.  
  
 Esta regla se desencadena cuando la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es excesivamente alta en comparación con el tiempo total de procesamiento de la aplicación.  
  
> [!NOTE]
>  Cuando la proporción de tiempo que se invierte en la recolección de elementos no utilizados es considerable, pero no excesiva, en comparación con el tiempo total de procesamiento de la aplicación, la advertencia [DA0023: Tiempo elevado de CPU de GC](../profiling/da0023-high-gc-cpu-time.md) se desencadena en lugar de esta regla.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque la columna **Memoria CLR de .NET\\% de tiempo del GC**. Determine si hay fases concretas de ejecución del programa en que la sobrecarga de la recolección de elementos no utilizados de memoria administrada sea mayor que en otras. Compare los valores de % de tiempo del GC con la tasa de recolección de elementos no utilizados notificada en los valores **N.º de colecciones de gen. 0**, **N.º de colecciones de gen. 1** y **N.º de colecciones de gen. 2**.  
  
 El valor del % de tiempo del GC intenta notificar la cantidad de tiempo que una aplicación dedica a la recolección de elementos no utilizados proporcional a la cantidad total de procesamiento. Tenga en cuenta que hay circunstancias en que el % de tiempo del GC puede notificar un valor muy alto, pero no es debido a una excesiva recolección de elementos no utilizados. Para obtener más información sobre la forma en que se calcula el valor del % de tiempo del GC, consulte la entrada [Diferencia entre los datos de rendimiento notificados por distintas herramientas – 4](http://go.microsoft.com/fwlink/?LinkId=177863) del **Weblog de Maoni** en MSDN. Si se producen errores de página o la aplicación es adelantada por otro trabajo de mayor prioridad en el equipo durante la recolección de elementos no utilizados, el contador del % de tiempo del GC reflejará esos retrasos adicionales.



