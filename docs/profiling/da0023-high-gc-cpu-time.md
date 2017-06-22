---
title: 'DA0023: Tiempo elevado de CPU de GC | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: f6c92673d3e8e1db37d547a466dcee127f190ca5
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="da0023-high-gc-cpu-time"></a>DA0024: Tiempo elevado de CPU de GC
|||  
|-|-|  
|Identificador de regla|DA0023|  
|Categoría|Uso de .NET Framework|  
|Método de generación de perfiles|Todas|  
|Mensaje|El % de tiempo del GC es bastante alto. Esta indicación de una cantidad excesiva de sobrecarga de la recolección de elementos no utilizados podría estar afectando a la capacidad de respuesta de la aplicación. Puede recopilar datos de asignación de memoria de .NET e información de vigencia del objeto para entender el patrón de asignación de memoria que la aplicación utiliza mejor.|  
|Tipo de regla|Informativa|  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es considerable en comparación con el tiempo total de procesamiento de la aplicación.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Run-time (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que utiliza un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no utiliza. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de una manera muy eficaz. Los objetos de la generación 1 se recopilan con menos frecuencia y, normalmente, de una manera menos eficaz. Por último, los objetos de larga duración de la generación 2 se deben recopilar incluso con menos frecuencia. La colección de la generación 2, que es una ejecución de recolección de elementos no utilizados completa, es también la operación más costosa.  
  
 Esta regla se desencadena cuando la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es considerable en comparación con el tiempo total de procesamiento de la aplicación.  
  
> [!NOTE]
>  Cuando la proporción de tiempo que se invierte en la recolección de elementos no utilizados es excesiva en comparación con el tiempo total de procesamiento de la aplicación, la advertencia [DA0024: Tiempo excesivo de CPU de GC](../profiling/da0024-excessive-gc-cpu-time.md) se desencadena en lugar de esta regla.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque la columna **Memoria CLR de .NET\\% de tiempo del GC**. Determine si hay fases concretas de ejecución del programa en que la sobrecarga de la recolección de elementos no utilizados de memoria administrada sea mayor que en otras. Compare los valores de % de tiempo del GC con la tasa de recolección de elementos no utilizados notificada en los valores **N.º de colecciones de gen. 0**, **N.º de colecciones de gen. 1** y **N.º de colecciones de gen. 2**.  
  
 El valor del % de tiempo del GC intenta notificar la cantidad de tiempo que una aplicación dedica a la recolección de elementos no utilizados proporcional a la cantidad total de procesamiento. Tenga en cuenta que hay circunstancias en que el % de tiempo del GC puede notificar un valor muy alto, pero no es debido a una excesiva recolección de elementos no utilizados. Para obtener más información sobre la manera en que se calcula el valor del % de tiempo del GC, vea la entrada [Diferencia entre los datos de rendimiento notificados por distintas herramientas – 4](http://go.microsoft.com/fwlink/?LinkId=177863) del **Weblog de Maoni** en MSDN. Si se producen errores de página o la aplicación es adelantada por otro trabajo de mayor prioridad en el equipo durante la recolección de elementos no utilizados, el contador del % de tiempo del GC reflejará esos retrasos adicionales.
