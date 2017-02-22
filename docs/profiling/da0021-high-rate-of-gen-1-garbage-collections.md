---
title: "DA0021: Alta frecuencia de recolecci&#243;n de elementos no utilizados de gen 1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0021: Alta frecuencia de recolecci&#243;n de elementos no utilizados de gen 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0021|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Todos|  
|Mensaje|Hay una frecuencia relativamente alta de recolección de elementos no utilizados de gen. 1.  Si, por diseño, la mayor parte de las estructuras de datos del programa se asignan y persisten durante mucho tiempo, no suele ser un problema.  Sin embargo, si este comportamiento no es intencionado, su aplicación puede estar anclando objetos.  Si no está seguro, puede recopilar datos de asignación de memoria de .NET e información de la duración de los objetos para entender el modelo de asignación de memoria que su aplicación utiliza.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que se recuperó una proporción considerable de la memoria de los objetos de .NET Framework en la recolección de elementos no utilizados de la generación 1 en comparación con la recolección de datos de la generación 0.  
  
## Descripción de la regla  
 Common Language Runtime \(CLR\) de Microsoft .NET proporciona un mecanismo de administración automática de la memoria que usa un recolector de elementos no utilizados para reclamar la memoria de los objetos que la aplicación ya no utiliza.  El recolector de elementos no utilizados está orientado a la generación y se basa en la suposición de que muchas asignaciones son de corta duración.  Las variables locales, por ejemplo, deben ser de corta duración.  Los objetos recién creados comienzan en la generación 0 \(gen 0\), progresan a la generación 1 cuando sobreviven a una ejecución de la recolección de elementos no utilizados y, finalmente, pasan a la generación 2 si la aplicación todavía los usa.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de manera muy eficiente.  Los objetos de la generación 1 se recopilan con menos frecuencia y de manera menos eficiente.  Por último, los objetos de larga duración de la generación 2 se deben recopilar con menos frecuencia.  La recolección de generación 2, que es una ejecución completa de la recolección de elementos no utilizados, es también la operación más costosa.  
  
 Esta regla se desencadena cuando proporcionalmente se han producido demasiadas recolecciones de elementos no utilizados de generación 1.  Si han sobrevivido demasiado pocos objetos de corta duración a la recolección de generación 0 pero pueden ser recolectados en una recolección de generación 1, el costo de administración de memoria se puede volver excesivo.  Para obtener más información, vea [Crisis de la media vida](http://go.microsoft.com/fwlink/?LinkId=177835) el envío en Rico mariani's performance Tidbits en el sitio web de MSDN.  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a [Vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque las columnas **Memoria de .NET CLR\\Número de colecciones de gen. 0** y **Memoria de .NET CLR\\Número de colecciones de gen. 1**.  Determine si hay fases concretas de ejecución de programas en las que la recolección de elementos no utilizados se está produciendo con más frecuencia.  Compare estos valores con la columna **% de tiempo del GC** para ver si el modelo de asignaciones de memoria administradas está provocando una sobrecarga excesiva de administración de memoria.  
  
 Para entender el modelo de utilización de memoria administrada de la aplicación, vuelva a generar sus perfiles ejecutando una generación de perfiles de asignación de memoria de .NET y solicite las mediciones de Duración del objeto.  
  
 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, vea [Recolector de elementos no utilizados Basics y sugerencias de rendimiento](http://go.microsoft.com/fwlink/?LinkId=148226) en el sitio web de Microsoft.  Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, vea [Montón de objetos grandes destapada](http://go.microsoft.com/fwlink/?LinkId=177836).