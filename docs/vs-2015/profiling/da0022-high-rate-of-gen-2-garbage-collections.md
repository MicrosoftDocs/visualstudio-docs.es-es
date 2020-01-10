---
title: 'DA0022: Alta frecuencia de recolección de elementos no utilizados de gen 2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0dcfa4d3522d88b58e971c0a4ff3f27649c2d21b
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844629"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Alta frecuencia de recolección de elementos no utilizados de gen 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identificador de regla | DA0022 |  
| Categoría |. Uso de .NET Framework |  
| Método de generación de perfiles | Todo |  
| Mensaje | Hay una frecuencia bastante alta de recolección de elementos no utilizados de gen 2. Si, por diseño, la mayoría de las estructuras de datos del programa se asignan y se conservan durante mucho tiempo, esto no es normalmente un problema. Sin embargo, si este comportamiento no es intencionado, su aplicación puede estar anclando objetos. Si no está seguro, puede recopilar datos de asignación de memoria de .NET e información de duración de objetos para entender el patrón de asignación de memoria que usa la aplicación.|  
| Tipo de regla | ADVERTENCIA |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que se recuperó una proporción considerable de la memoria para los objetos de .NET Framework en la generación 2 de recolección de elementos no utilizados en comparación con la recolección de elementos no utilizados de las generaciones 0 y 1.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Run-time (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que utiliza un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no utiliza. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de una manera muy eficaz. Los objetos de la generación 1 se recopilan con menos frecuencia y, normalmente, de una manera menos eficaz. Por último, los objetos de larga duración de la generación 2 se deben recopilar incluso con menos frecuencia. La colección de la generación 2, que es una ejecución de recolección de elementos no utilizados completa, es también la operación más costosa.  
  
 Esta regla se desencadena cuando se ha producido proporcionalmente demasiada recolección de elementos no utilizados de la generación 2. En las aplicaciones .NET Framework que exhiben un buen comportamiento, la recolección de elementos no utilizados de la generación 1 se producirá 5 veces más que la colección de la generación 2. (Un factor 10x es probablemente ideal).  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque las columnas **Memoria CLR de .NET\\N.º de colecciones de gen. 0** y **Memoria CLR de .NET\\N.º de colecciones de gen. 1**. Determine si hay fases concretas de ejecución del programa en que la recolección de datos no utilizados se produzca con mayor frecuencia. Compare estos valores con la columna **% de tiempo del GC** para ver si el patrón de las asignaciones de memoria administrada está provocando una sobrecarga de administración de memoria excesiva.  
  
 Una proporción alta de recolección de elementos no utilizados de la generación 2 no siempre es un problema. Podría ser por diseño. Una aplicación que asigne estructuras de datos grandes que deban permanecer activas durante largos períodos durante la ejecución puede desencadenar esta regla. Cuando este tipo de aplicación está bajo presión de memoria, podría verse obligada a realizar con frecuencia la recolección de elementos no utilizados. Si la recolección de elementos no utilizados de las generaciones 0 y 1, menos costosa, puede reclamar solo una pequeña cantidad de memoria administrada, se programará con mayor frecuencia la recolección de elementos no utilizados de la generación 2.  
  
 Hay columnas de memoria de .NET CLR adicionales en la vista Marcas que pueden ayudarlo a identificar los problemas de la recolección de elementos no utilizados. La columna **% de tiempo del GC** lo ayudará a comprender cuánta sobrecarga de administración de memoria se está produciendo. Si su aplicación normalmente utiliza un número bastante pequeño de objetos grandes, pero persistentes, las colecciones de la generación 2 frecuentes no deberían consumir cantidades excesivas de tiempo de CPU. Si la aplicación está bajo presión de memoria porque se requiere más memoria física (RAM), las reglas relacionadas que evalúan los valores de la columna **Memory\Pages/sec** también se pueden desencadenar.  
  
 Para entender el patrón de uso de memoria administrada de la aplicación, vuelva a generar perfiles de la aplicación mediante una ejecución de generación de perfiles de asignación de memoria de .NET y seleccione la opción de generación de perfiles de la vigencia del objeto.  
  
 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, consulte [Aspectos básicos e indicaciones de rendimiento del recolector de elementos no utilizados](https://msdn2.microsoft.com/library/ms973837.aspx) en el sitio web de MSDN. Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, consulte [Montón de objeto grande al descubierto](https://msdn.microsoft.com/magazine/cc534993.aspx).
