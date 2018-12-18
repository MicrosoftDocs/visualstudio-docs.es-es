---
title: 'DA0005: Colecciones GC2 frecuentes | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5e3038f873895e38cf162e67316bc08f2fc007b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849379"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Colecciones GC2 frecuentes

|||  
|-|-|  
|RuleId|DA0005|  
|Categoría|Uso de .NET Framework|  
|Método de generación de perfiles|Memoria de .NET|  
|Mensaje|Muchos de los objetos se están recolectando mediante la recolección de elementos no utilizados de generación 2.|  
|Tipo de mensaje|Advertencia|  

## <a name="cause"></a>Motivo  
 Se está recuperando un número elevado de objetos de memoria de .NET en la recolección de elementos no utilizados de la generación 2.  

## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Runtime (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que usa un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no usa. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  

 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de una manera muy eficaz. Los objetos de la generación 1 se recopilan con menos frecuencia y, normalmente, de una manera menos eficaz. Por último, los objetos de larga duración de la generación 2 se deben recopilar incluso con menos frecuencia. La colección de la generación 2, que es una ejecución de recolección de elementos no utilizados completa, es también la operación más costosa.  

 Esta regla se desencadena cuando se ha producido proporcionalmente demasiada recolección de elementos no utilizados de la generación 2. Si relativamente demasiados objetos de corta duración sobreviven a la colección de generación 1, pero pueden ser recopilados en una colección completa de generación 2, el costo de la administración de memoria se puede volver excesivo con facilidad. Para obtener más información, consulte la publicación [Crisis de vida media](http://go.microsoft.com/fwlink/?LinkId=177835) en los alicientes de rendimiento de Rico Mariani en el sitio web de MSDN.  

## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Revise los informes [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md) para entender el patrón de asignación de memoria de la aplicación. Use la [vista Duración del objeto](../profiling/object-lifetime-view.md) para determinar cuáles de los objetos de datos del programa sobreviven a la generación 2 y, después, se recuperan desde allí. Utilice la [vista Asignaciones](../profiling/dotnet-memory-allocations-view.md) para determinar la ruta de acceso de ejecución que dio lugar a estas asignaciones.  

 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, consulte [Aspectos básicos e indicaciones de rendimiento del recolector de elementos no utilizados](http://go.microsoft.com/fwlink/?LinkId=148226) en el sitio web de MSDN. Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, consulte [Montón de objeto grande al descubierto](http://go.microsoft.com/fwlink/?LinkId=177836).