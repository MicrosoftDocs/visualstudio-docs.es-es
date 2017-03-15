---
title: "DA0005: Colecciones GC2 frecuentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0005: Colecciones GC2 frecuentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0005|  
|Categoría|Uso de .NET Framework|  
|Método de generación de perfiles|Memoria de .NET|  
|Mensaje|Muchos de los objetos se están recolectando mediante recolección de elementos no utilizados de generación 2.|  
|Tipo de mensaje|Advertencia|  
  
## Motivo  
 Se está recuperando un gran número de objetos de memoria de .NET en la recolección de elementos no utilizados de la generación 2.  
  
## Descripción de la regla  
 Common Language Runtime \(CLR\) de Microsoft .NET proporciona un mecanismo de administración automática de la memoria que usa un recolector de elementos no utilizados para reclamar la memoria de los objetos que la aplicación ya no utiliza.  El recolector de elementos no utilizados está orientado a la generación y se basa en la suposición de que muchas asignaciones son de corta duración.  Las variables locales, por ejemplo, deben ser de corta duración.  Los objetos recién creados comienzan en la generación 0 \(gen 0\), progresan a la generación 1 cuando sobreviven a una ejecución de la recolección de elementos no utilizados y, finalmente, pasan a la generación 2 si la aplicación todavía los usa.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de manera muy eficiente.  Los objetos de la generación 1 se recopilan con menos frecuencia y de manera menos eficiente.  Por último, los objetos de larga duración de la generación 2 se deben recopilar con menos frecuencia.  La recolección de generación 2, que es una ejecución completa de la recolección de elementos no utilizados, es también la operación más costosa.  
  
 Esta regla se desencadena cuando proporcionalmente se han producido demasiadas recolecciones de elementos no utilizados de generación 2.  Si relativamente demasiados objetos de corta duración sobreviven a la colección de generación 1, pero pueden ser recopilados en una colección completa de generación 2, el costo de la administración de memoria se puede volver excesivo con facilidad.  Para obtener más información, vea [Crisis de la media vida](http://go.microsoft.com/fwlink/?LinkId=177835) el envío en Rico mariani's performance Tidbits en el sitio web de MSDN.  
  
## Cómo investigar una advertencia  
 Revise los informes [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md) para entender el modelo de asignación de memoria de la aplicación.  Use la [Vista Duración del objeto](../profiling/object-lifetime-view.md) para determinar qué objetos de datos del programa sobreviven a la generación 2 y, a continuación, se recuperan desde allí.  Utilice la [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md) para determinar la ruta de acceso de ejecución que daba lugar a estas asignaciones.  
  
 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, vea [Recolector de elementos no utilizados Basics y sugerencias de rendimiento](http://go.microsoft.com/fwlink/?LinkId=148226) en el sitio web de Microsoft.  Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, vea [Montón de objetos grandes destapada](http://go.microsoft.com/fwlink/?LinkId=177836).