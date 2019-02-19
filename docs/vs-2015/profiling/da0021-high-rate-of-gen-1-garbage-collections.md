---
title: 'DA0021: Alta frecuencia de recolección de elementos no utilizados de gen 1 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a4502be6c683376b93bc144ef5b3568550a1c9e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834356"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Alta frecuencia de recolección de elementos no utilizados de gen 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0021 |  
| Categoría |. Uso de .NET Framework |  
| Métodos de generación de perfiles | Todos los |  
| Mensaje | Hay una frecuencia relativamente alta de elementos no utilizados de Gen 1 que se producen. Si, por diseño, la mayoría de las estructuras de datos del programa se asignan y se conservan durante mucho tiempo, esto no es normalmente un problema. Sin embargo, si este comportamiento no es intencionado, su aplicación puede estar anclando objetos. Si no está seguro, puede recopilar datos de asignación de memoria de .NET e información de duración de objetos para entender el patrón de asignación de memoria que usa la aplicación.|  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que se recuperó una proporción considerable de la memoria para los objetos de .NET Framework en la generación 1 de recolección de elementos no utilizados en comparación con la generación 0 de colección de datos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Run-time (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que utiliza un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no utiliza. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de una manera muy eficaz. Los objetos de la generación 1 se recopilan con menos frecuencia y, normalmente, de una manera menos eficaz. Por último, los objetos de larga duración de la generación 2 se deben recopilar incluso con menos frecuencia. La colección de la generación 2, que es una ejecución de recolección de elementos no utilizados completa, es también la operación más costosa.  
  
 Esta regla se desencadena cuando se ha producido proporcionalmente demasiada recolección de elementos no utilizados de la generación 1. Si hay demasiados objetos de relativamente corta duración que sobreviven a la colección de la generación 0, pero después pueden recopilarse en una colección de la generación 1, el coste de administración de memoria puede ser excesivo. Para obtener más información, consulte la publicación [Crisis de vida media](http://go.microsoft.com/fwlink/?LinkId=177835) en los alicientes de rendimiento de Rico Mariani en el sitio web de MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque las columnas **Memoria CLR de .NET\\N.º de colecciones de gen. 0** y **Memoria CLR de .NET\\N.º de colecciones de gen. 1**. Determine si hay fases concretas de ejecución del programa en que la recolección de datos no utilizados se produzca con mayor frecuencia. Compare estos valores con la columna **Porcentaje de tiempo del GC** para ver si el patrón de las asignaciones de memoria administrada está provocando una sobrecarga de administración de memoria excesiva.  
  
 Para entender el patrón de uso de memoria administrada de la aplicación, vuelva a generar perfiles de la aplicación mediante una ejecución de generación de perfiles de asignación de memoria de .NET y solicite mediciones de duración de objetos.  
  
 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, consulte [Aspectos básicos e indicaciones de rendimiento del recolector de elementos no utilizados](http://go.microsoft.com/fwlink/?LinkId=148226) en el sitio web de MSDN. Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, consulte [Montón de objeto grande al descubierto](http://go.microsoft.com/fwlink/?LinkId=177836).
