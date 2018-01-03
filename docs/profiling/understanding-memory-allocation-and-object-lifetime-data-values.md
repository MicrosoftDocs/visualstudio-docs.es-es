---
title: "Descripción de los valores de datos de asignación de memoria y duración de objetos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eade1af6d21d4068d96f021d43f60c0ca38bb33c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Descripción de los valores de datos de asignación de memoria y duración de objetos
El método de generación de perfiles *Asignación de memoria .NET* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recopila información sobre el tamaño y el número de objetos que se crearon en una asignación o se destruyeron en una recolección de elementos no utilizados e información adicional sobre la *pila de llamadas* de la función cuando se produjo el evento. Una *pila de llamadas* es una estructura dinámica que almacena información sobre las funciones que se ejecutan en el procesador.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 El generador de perfiles de memoria interrumpe el procesador del equipo en cada asignación de un objeto de .NET Framework en una aplicación cuyos perfiles se están generando. Cuando también se recopilan datos de duración de objetos, el generador de perfiles interrumpe el procesador después de cada recolección de elementos no utilizados de .NET Framework. Los datos se agregan para cada función de la que se generan perfiles y para cada tipo de objeto.  
  
## <a name="allocation-data"></a>Datos de asignación  
 Cuando se produce un evento .memory, se incrementan los recuentos totales y los tamaños de los objetos de memoria asignados o destruidos.  
  
 Cuando se produce un evento de asignación .memory, el generador de perfiles incrementa los recuentos de muestras para cada función en la pila de llamadas. Cuando se recopilan los datos, solo una función en la pila de llamadas está ejecutando el código en el cuerpo de la función. Las demás funciones de la pila son elementos primarios en la jerarquía de llamadas de función que están esperando a que las funciones que llamaron devuelvan información.  
  
-   Para el evento de asignación, el generador de perfiles incrementa la muestra *exclusiva* del recuento de la función que está ejecutando actualmente sus instrucciones. Dado que una muestra exclusiva también forma parte de las muestras totales (*inclusivas*) de la función, también se incrementa el recuento de muestras inclusivas de la función actualmente activa.  
  
-   El generador de perfiles incrementa el recuento de muestras inclusivas de todas las demás funciones en la pila de llamadas.  
  
## <a name="lifetime-data"></a>Datos de duración  
 El recolector de elementos no utilizados de .NET Framework administra la asignación y liberación de la memoria de la aplicación. Para optimizar el rendimiento del recolector de elementos no utilizados, el montón administrado se divide en tres generaciones: 0, 1 y 2. El recolector de elementos no utilizados del runtime almacena los nuevos objetos en la generación 0. Los objetos que sobreviven a las recopilaciones se promueven y almacenan en las generaciones 1 y 2.  
  
 El recolector de elementos no utilizados recupera memoria desasignando una generación completa de objetos. Para los objetos creados por la aplicación de la que se generaron perfiles, la vista Duración del objeto muestra el número y tamaño de los objetos y la generación cuando se recuperan.