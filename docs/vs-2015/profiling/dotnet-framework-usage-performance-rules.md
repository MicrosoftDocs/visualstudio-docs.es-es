---
title: Reglas de rendimiento de uso de .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f1fee0c059189c2a120dfb83556ec94f119a2f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197631"
---
# <a name="net-framework-usage-performance-rules"></a>Reglas de rendimiento de uso de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las reglas de rendimiento de la categoría de uso de .NET Framework identifican los métodos específicos que se pueden optimizar, así como los patrones de uso más generales, como la recolección de elementos no utilizados y la contención de bloqueo, que se pueden investigar para detectar problemas de rendimiento.  
  
|||  
|-|-|  
|[DA0001: Use StringBuilder para concatenaciones](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Las llamadas a <xref:System.String.Concat%28System.String%2CSystem.String%29?displayProperty=fullName> constituyen una proporción considerable de los datos de generación de perfiles. Considere la posibilidad de usar la clase <xref:System.Text.StringBuilder> para construir cadenas a partir de varios segmentos.|  
|[DA0005: Colecciones GC2 frecuentes](../profiling/da0005-frequent-gc2-collections.md)|Se está recuperando un número relativamente elevado de objetos de memoria de .NET en la recolección de elementos no utilizados de la generación 2. Si hay demasiados objetos de corta duración que sobreviven a la colección de la generación 1, es fácil que el coste de administración de memoria se vuelva excesivo.|  
|[DA0006: Invalidar Equals() para tipos de valor](../profiling/da0006-override-equals-parens-for-value-types.md)|Las llamadas al método `Equals` o los operadores de igualdad de un tipo de valor público constituyen una proporción considerable de los datos de generación de perfiles. Considere la posibilidad de implementar un método más eficaz.|  
|[DA0007: Evite utilizar excepciones para el flujo de control](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Se produjo una alta tasa de controladores de excepciones de .NET Framework en los datos de generación de perfiles. Puede utilizar otra lógica de flujo de control para reducir el número de excepciones que se producen.|  
|[DA0010: Función GetHashCode que consume muchos recursos](../profiling/da0010-expensive-gethashcode.md)|Las llamadas al método `GetHashCode` del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método `GetHashCode` asigna memoria. Reduzca la complejidad del método.|  
|[DA0011: Función CompareTo que consume muchos recursos](../profiling/da0011-expensive-compareto.md)|El método `CompareTo` del tipo es costoso o el método asigna memoria. Reduzca la complejidad del método `CompareTo`.|  
|[DA0012: Cantidad significativa de reflexión](../profiling/da0012-significant-amount-of-reflection.md)|Las llamadas a métodos <xref:System.Reflection?displayProperty=fullName>, como <xref:System.Reflection.IReflect.InvokeMember%2A> y <xref:System.Reflection.IReflect.GetMember%2A>, o a métodos Type, como <xref:System.Type.InvokeMember%2A>, constituyen una proporción considerable de los datos de generación de perfiles. Cuando sea posible, considere la posibilidad de reemplazar estos métodos con enlace anticipado a los métodos de ensamblados dependientes.|  
|[DA0013: Uso elevado de String.Split/String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Las llamadas a los métodos <xref:System.String.Split%2A?displayProperty=fullName> o <xref:System.String.Substring%2A> constituyen una proporción considerable de los datos de generación de perfiles. Considere la opción de usar <xref:System.String.IndexOf%2A> o <xref:System.String.IndexOfAny%2A> si va a probar la existencia de una subcadena en una cadena.|  
|[DA0018: Aplicación de 32 bits ejecutándose con límites de memoria administrada de procesos](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Los datos del sistema recopilados durante la ejecución de generación de perfiles indican que los montones de memoria de .NET Framework se aproximaron al tamaño máximo que los montones administrados pueden alcanzar en un proceso de 32 bits. Considere la posibilidad de volver a generar perfiles mediante el método de generación de perfiles de memoria de .NET y optimizar el uso de recursos administrados por la aplicación.|  
|[DA0021: Alta frecuencia de recolección de elementos no utilizados de gen. 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Se está recuperando un número relativamente elevado de objetos de memoria de .NET en la recolección de elementos no utilizados de la generación 1. Si hay demasiados objetos de corta duración que sobreviven a la colección de la generación 0, el coste de administración de memoria puede ser fácilmente excesivo.|  
|[DA0022: Alta frecuencia de recolección de elementos no utilizados de gen. 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Se está recuperando un número elevado de objetos de memoria de .NET en la recolección de elementos no utilizados de la generación 2. Si hay demasiados objetos de corta duración que sobreviven a la colección de la generación 1, es fácil que el coste de administración de memoria se vuelva excesivo. Esta regla se desencadena cuando la tasa de contenciones de bloqueo supera el valor de umbral superior de la regla DA0005.|  
|[DA0023: Mucho tiempo de CPU de GC](../profiling/da0023-high-gc-cpu-time.md)|Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es considerable en comparación con el tiempo total de procesamiento de la aplicación.|  
|[DA0024: Tiempo excesivo de CPU de GC](../profiling/da0024-excessive-gc-cpu-time.md)|Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que la cantidad de tiempo que se invierte en la recolección de elementos no utilizados es excesivamente alta en comparación con el tiempo total de procesamiento de la aplicación. Esta regla se desencadena cuando la cantidad de tiempo invertido en la recolección de elementos no utilizados supera el valor de umbral superior de la regla DA0023.|  
|[DA0038: Alta frecuencia de contenciones de bloqueo](../profiling/da0038-high-rate-of-lock-contentions.md)|Los datos de rendimiento del sistema recopilados con los datos de generación de perfiles indican que se produjo una tasa considerablemente alta de contenciones de bloqueo durante la ejecución de la aplicación. Considere la posibilidad de volver a generar perfiles con el método de generación de perfiles de simultaneidad para encontrar la causa de las contenciones.|  
|[DA0039: Alta frecuencia de contenciones de bloqueo](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Los datos de rendimiento del sistema recopilados con los datos de generación de perfiles indican que se produjo una tasa excesivamente alta de contenciones de bloqueo durante la ejecución de la aplicación. Considere la posibilidad de volver a generar perfiles con el método de generación de perfiles de simultaneidad para encontrar la causa de las contenciones. Esta regla se desencadena cuando la tasa de contenciones de bloqueo supera el valor de umbral superior de la regla DA0038.|



