---
title: "DA0022: Alta frecuencia de recolecci&#243;n de elementos no utilizados de gen 2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0022"
  - "vs.performance.rules.DA0022"
  - "vs.performance.22"
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0022: Alta frecuencia de recolecci&#243;n de elementos no utilizados de gen 2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0022|  
|Categoría|Uso de .NET Framework|  
|Método de generación de perfiles|Todos|  
|Mensaje|Hay una frecuencia relativamente alta de recolección de elementos no utilizados de gen. 2.  Si, por diseño, la mayor parte de las estructuras de datos del programa se asignan y persisten durante mucho tiempo, no suele ser un problema.  Sin embargo, si este comportamiento no es intencionado, su aplicación puede estar anclando objetos.  Si no está seguro, puede recopilar datos de asignación de memoria de .NET e información de la duración de los objetos para entender el modelo de asignación de memoria que su aplicación utiliza.|  
|Tipo de regla|Advertencia|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que se recuperó una proporción considerable de la memoria de los objetos de .NET Framework en la recolección de elementos no utilizados de la generación 2 en comparación con la recolección de elementos no utilizados de la generación 0 y la 1.  
  
## Descripción de la regla  
 Common Language Runtime \(CLR\) de Microsoft .NET proporciona un mecanismo de administración automática de la memoria que usa un recolector de elementos no utilizados para reclamar la memoria de los objetos que la aplicación ya no utiliza.  El recolector de elementos no utilizados está orientado a la generación y se basa en la suposición de que muchas asignaciones son de corta duración.  Las variables locales, por ejemplo, deben ser de corta duración.  Los objetos recién creados comienzan en la generación 0 \(gen 0\), progresan a la generación 1 cuando sobreviven a una ejecución de la recolección de elementos no utilizados y, finalmente, pasan a la generación 2 si la aplicación todavía los usa.  
  
 Los objetos de la generación 0 se recopilan con frecuencia y, normalmente, de manera muy eficiente.  Los objetos de la generación 1 se recopilan con menos frecuencia y de manera menos eficiente.  Por último, los objetos de larga duración de la generación 2 se deben recopilar con menos frecuencia.  La recolección de generación 2, que es una ejecución completa de la recolección de elementos no utilizados, es también la operación más costosa.  
  
 Esta regla se desencadena cuando proporcionalmente se producen demasiadas recolecciones de elementos no utilizados de generación 2.  Las aplicaciones .NET Framework con buen comportamiento tendrán cinco veces más recolecciones de elementos no utilizados de generación 1 que de generación 2. \(Lo ideal probablemente sea un factor 10\).  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a [Vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque las columnas **Memoria de .NET CLR\\Número de colecciones de gen. 0** y **Memoria de .NET CLR\\Número de colecciones de gen. 1**.  Determine si hay fases concretas de ejecución de programas en las que la recolección de elementos no utilizados se está produciendo con más frecuencia.  Compare estos valores con la columna **% de tiempo del GC** para ver si el modelo de asignaciones de memoria administradas está provocando una sobrecarga excesiva de administración de memoria.  
  
 Una proporción alta de recolecciones de elementos no utilizados de generación 2 no siempre supone un problema.  Podría ser por diseño.  Una aplicación que asigne estructuras de datos grandes que deban permanecer activas durante largos períodos durante la ejecución puede desencadenar esta regla.  Cuando una aplicación de este tipo está bajo presión de memoria, podría verse obligada a realizar recolecciones de elementos no utilizados frecuentes.  Si las recolecciones de elementos no utilizados de generación 0 y 1 que consumen menos recursos pueden reclamar solo una cantidad pequeña de memoria administrada, se programarán recolecciones de elementos no utilizados de generación 2 más frecuentes.  
  
 En la vista Marcas hay columnas Memoria .NET CLR adicionales que pueden ayudarle a identificar problemas de recolección de elementos no utilizados.  La columna **% de tiempo del GC** le ayuda a entender cuánta sobrecarga de administración de memoria se está produciendo.  Si su aplicación normalmente utiliza un número bastante pequeño de objetos grandes aunque persistentes, las recolecciones de generación 2 no deberían consumir cantidades excesivas de tiempo de la CPU.  Si la aplicación está bajo presión de memoria porque se necesita más memoria física \(RAM\), las reglas relacionadas que evalúan los valores de la columna **Memoria\\Páginas por segundo** también pueden desencadenarse.  
  
 Para entender el modelo de utilización de memoria administrada de la aplicación, vuelva a generar sus perfiles ejecutando una generación de perfiles de asignación de memoria de .NET y seleccione la opción de generación de perfiles Duración del objeto.  
  
 Para obtener información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, vea [Recolector de elementos no utilizados Basics y sugerencias de rendimiento](http://go.microsoft.com/fwlink/?LinkId=148226) en el sitio web de Microsoft.  Para obtener información sobre la sobrecarga de recolección de elementos no utilizados automática, vea [Montón de objetos grandes destapada](http://go.microsoft.com/fwlink/?LinkId=177836).