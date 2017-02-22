---
title: "DA0018: Una aplicaci&#243;n de 32 bits se est&#225; ejecutando en l&#237;mites de memoria administrados del proceso | Microsoft Docs"
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
  - "vs.performance.18"
  - "vs.performance.DA0018"
  - "vs.performance.rules.DA0018"
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0018: Una aplicaci&#243;n de 32 bits se est&#225; ejecutando en l&#237;mites de memoria administrados del proceso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0018|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Método de generación de perfiles|Muestreo|  
|Mensaje|Las asignaciones de memoria administradas se están aproximando al límite predeterminado para procesos de 32 bits.  Puede que la aplicación esté enlazada a memoria.|  
|Tipo de regla|Advertencia|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Motivo  
 Los datos del sistema recopilados durante la generación de perfiles indican que los montones de memoria de .NET Framework se aproximaron al tamaño máximo que los montones administrados pueden alcanzar en un proceso de 32 bits.  Este tamaño máximo es un valor predeterminado.  Está basado en la cantidad total del espacio de direcciones de proceso que se puede asignar para los bytes privados.  El valor notificado es el valor máximo de los montones observado mientras el proceso para el que se estaban generando los perfiles estaba activo.  Puede volver a generar los perfiles mediante el método de generación de perfiles de memoria de .NET y optimizando el uso de recursos administrados por parte de la aplicación.  
  
 Cuando el tamaño de los montones administrados se aproxima al límite predeterminado, es posible que se tenga que invocar al proceso de recolección de elementos no utilizados automático con más frecuencia.  Esto aumenta la sobrecarga de administración de memoria.  
  
 La regla solo se desencadena para las aplicaciones de 32 bits que se ejecutan en equipos de 32 bits.  
  
## Descripción de la regla  
 Common Language Runtime \(CLR\) de Microsoft .NET proporciona un mecanismo de administración automática de la memoria que usa un recolector de elementos no utilizados para reclamar la memoria de los objetos que la aplicación ya no utiliza.  El recolector de elementos no utilizados está orientado a la generación y se basa en la suposición de que muchas asignaciones son de corta duración.  Las variables locales, por ejemplo, deben ser de corta duración.  Los objetos recién creados comienzan en la generación 0 \(gen 0\), progresan a la generación 1 cuando sobreviven a una ejecución de la recolección de elementos no utilizados y, finalmente, pasan a la generación 2 si la aplicación todavía los usa.  
  
 Objetos administrados que son mayores de 85 KB se asignan en el montón de objetos grandes, donde están sujetos a la recolección de elementos no utilizados y compactaciones menos frecuentes que los objetos más pequeños. los objetos grandes se administran por separado porque se supone que son más persistentes y porque no se persistentes y grandes con objetos más pequeños con frecuencia asignados puede generar la fragmentación de la inservible\- conversión de la pila.  
  
 A medida que el tamaño total de los montones administrados se aproxima al límite predeterminado, la sobrecarga de administración de memoria suele aumentar hasta el punto de poder empezar a afectar a la respuesta y escalabilidad de la aplicación.  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md).  Busque las columnas **Memoria de .NET CLR\\Número de bytes en todos los montones** y **Número de bytes totales confirmados**.  Determine si hay fases concretas de la ejecución de programas en las que la asignación de memoria administrada sea mayor que en otras.  Compare los valores de la columna **Número de bytes en todos los montones** con la tasa de recolección de elementos no utilizados indicada en las columnas **Memoria de .NET CLR\\Número de colecciones de gen. 0**, **Memoria de .NET CLR\\Número de colecciones de gen. 1** y **Memoria de .NET CLR\\Número de colecciones de gen. 2** para determinar si el modelo de asignaciones de memoria administradas afecta a la tasa de recolección de elementos no utilizados.  
  
 En una aplicación .NET Framework, Common Language Runtime limita el tamaño total de los montones administrados a un poco menos de la mitad del tamaño máximo de la parte del área privada de un espacio de direcciones de proceso.  Para un proceso de 32 bits que se ejecuta en un equipo de 32 bits, 2 GB representa el límite superior de la parte privada del espacio de direcciones de proceso.  A medida que el tamaño total de los montones administrados empieza a aproximarse a su límite predeterminado, la sobrecarga de administración de memoria podría aumentar y el rendimiento de la aplicación disminuir.  
  
 Si la sobrecarga excesiva de administración de memoria supone un problema, considere cualquiera de estas opciones:  
  
-   optimizar el uso de recursos de memoria administrados de la aplicación  
  
     O bien  
  
-   tomar medidas para aligerar las restricciones arquitectónicas sobre el tamaño máximo de memoria virtual para un proceso de 32 bits  
  
 Para optimizar el uso de recursos de memoria administrados de la aplicación, recopile datos de asignación de memoria administrada en una generación de perfiles de asignación de memoria de .NET.  Revise los informes [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md) para entender el modelo de asignación de memoria de la aplicación.  
  
 Utilice la [Vista Duración del objeto](../profiling/object-lifetime-view.md) para determinar cuáles de los objetos de datos del programa sobreviven a la generación y a continuación se recuperan desde allí.  
  
 Utilice la [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md) para determinar la ruta de acceso de ejecución que daba lugar a estas asignaciones.  
  
 Para obtener más información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, vea el artículo técnico de .NET Framework, [Recolector de elementos no utilizados Basics y sugerencias de rendimiento](http://go.microsoft.com/fwlink/?LinkId=177946) en el sitio web de MSDN.  
  
 Para aligerar las restricciones de memoria virtual sobre el tamaño de la parte privada de un espacio de direcciones de proceso, intente ejecutar este proceso de 32 bits en un equipo de 64 bits.  Un proceso de 32 bits en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.  
  
 Un proceso de 64 bits en un equipo de 64 bits puede adquirir hasta 8 TB de memoria virtual.  Puede volver a compilar la aplicación para que se ejecute como una aplicación de 64 bits nativa.  Esta regla solo tiene un fin informativo y es posible que no necesite acción correctora alguna.