---
title: 'DA0018: Aplicación de 32 bits ejecutándose con límites de memoria administrada de procesos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6418a39d7e53a3edaa48b3cd003d35d95cba386e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773292"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: Una aplicación de 32 bits se está ejecutando en límites de memoria administrados del proceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0018 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Método de generación de perfiles | Muestreo |  
| Mensaje | Administrar las asignaciones de memoria que se está acercando al límite predeterminado para un proceso de 32 bits. Puede que la aplicación esté enlazada a la memoria.|  
| Tipo de regla | Advertencia |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos del sistema recopilados durante la ejecución de generación de perfiles indican que los montones de memoria de .NET Framework se aproximaron al tamaño máximo que los montones administrados pueden alcanzar en un proceso de 32 bits. Este tamaño máximo es un valor predeterminado. Se basa en la cantidad total de espacio de direcciones de proceso que se puede asignar para los bytes privados. El valor notificado es el valor máximo observado de los montones mientras estaba activo el proceso del que se generaron perfiles. Considere la posibilidad de volver a generar perfiles mediante el método de generación de perfiles de memoria de .NET y optimizar el uso de recursos administrados por la aplicación.  
  
 Cuando el tamaño de los montones administrados se aproxima al límite predeterminado, tal vez deba invocarse el proceso de recolección de elementos no utilizados automática con más frecuencia. Esto aumenta la sobrecarga de administración de memoria.  
  
 La regla solo se desencadena para aplicaciones de 32 bits que se ejecutan en equipos de 32 bits.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El Common Language Run-time (CLR) de Microsoft .NET proporciona un mecanismo de administración de memoria automática que utiliza un recolector de elementos no utilizados para reclamar memoria de los objetos que la aplicación ya no utiliza. El recolector de elementos no utilizados está orientado a la generación, según la suposición de que muchas asignaciones son de corta duración. Las variables locales, por ejemplo, deben ser de corta duración. Los objetos recién creados comienzan en la generación 0 (gen 0), a continuación avanzan hacia la generación 1 cuando sobreviven a una ejecución de recopilación de elementos no utilizados y, finalmente, hacen una transición a la generación 2 si la aplicación todavía los utiliza.  
  
 Los objetos administrados mayores de 85 KB se asignan al montón de objetos grandes, en que la recolección de elementos no utilizados y la compactación se realiza con menos frecuencia que en el caso de objetos de menor tamaño. Los objetos grandes se administran por separado porque se supone que son más persistentes y porque mezclar objetos persistentes y grandes con objetos de menor tamaño asignados con frecuencia puede producir una peor conversión de la fragmentación del montón.  
  
 A medida que el tamaño total de los montones administrados se aproxima al límite predeterminado, la sobrecarga de administración de memoria suele aumentar hasta el punto en que puede comenzar a afectar a la capacidad de respuesta y la escalabilidad de la aplicación.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md). Busque las columnas **Memoria de .NET CLR\\, Número de bytes en todos los montones** y **Número de bytes totales confirmados**. Determine si hay fases concretas de ejecución del programa en que la asignación de memoria administrada sea mayor que en otras. Compare los valores de la columna **Número de bytes en todos los montones** con la tasa de recolección de elementos no utilizados notificada en las columnas **Memoria CLR de .NET\\N.º de colecciones de gen. 0**, **Memoria CLR de .NET\\N.º de colecciones de gen. 1** y **Memoria CLR de .NET\\N.º de colecciones de gen. 2** para determinar si el patrón de las asignaciones de memoria administrada está afectando a la tasa de recolección de elementos no utilizados.  
  
 En una aplicación de .NET Framework, el Common Language Runtime limita el tamaño total de los montones administrados a un poco menos de la mitad del tamaño máximo de la parte del área privada de un espacio de direcciones de proceso. Para los procesos de 32 bits que se ejecutan en un equipo de 32 bits, 2 GB representa el límite superior de la parte privada del espacio de direcciones de proceso. A medida que el tamaño total de los montones administrados empieza a aproximarse a su límite predeterminado, la sobrecarga de administración de memoria puede aumentar y el rendimiento de la aplicación puede disminuir.  
  
 Si la sobrecarga excesiva de memoria administrada es un problema, considere cualquiera de estas opciones:  
  
- optimizar el uso de la aplicación de recursos de memoria administrada  
  
   o bien  
  
- tomar medidas para aligerar las restricciones arquitectónicas sobre el tamaño máximo de memoria virtual para un proceso de 32 bits  
  
  Para optimizar el uso de recursos de memoria administrada de la aplicación, recopile datos de asignación de memoria administrada en una ejecución de generación de perfiles de asignación de memoria de .NET. Revise los informes [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md) para entender el patrón de asignación de memoria de la aplicación.  
  
  Utilice la [vista Duración del objeto](../profiling/object-lifetime-view.md) para determinar cuáles de los objetos de datos del programa sobreviven a la generación y, después, se recuperan desde allí.  
  
  Utilice la [vista Asignaciones](../profiling/dotnet-memory-allocations-view.md) para determinar la ruta de acceso de ejecución que dio lugar a estas asignaciones.  
  
  Para obtener más información sobre cómo mejorar el rendimiento de la recolección de elementos no utilizados, consulte el artículo técnico de .NET Framework [Aspectos básicos e indicaciones de rendimiento del recolector de elementos no utilizados](http://go.microsoft.com/fwlink/?LinkId=177946) en el sitio web de MSDN.  
  
  Para aligerar desde un punto de vista arquitectónico las restricciones de memoria virtual en el tamaño de la parte privada de un espacio de direcciones de proceso, intente ejecutar este proceso de 32 bits en un equipo de 64 bits.  Un proceso de 32 bits en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.  
  
  Un proceso de 64 bits ejecutado en un equipo de 64 bits puede adquirir hasta 8 GB de memoria virtual. Considere la posibilidad de volver a compilar la aplicación para ejecutarla como una aplicación nativa de 64 bits. Esta regla solo tiene un fin informativo y es posible que no necesite acción correctora alguna.
