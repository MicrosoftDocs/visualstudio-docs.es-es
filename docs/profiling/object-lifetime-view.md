---
title: "Vista Duraci&#243;n del objeto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "duración, objetos"
  - "Duración de objetos (vista)"
  - "informes de rendimiento, Duración de objetos (vista)"
  - "informes de herramientas de generación de perfiles, Duración (vista)"
  - "herramientas de generación de perfiles, Duración (vista)"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Duraci&#243;n del objeto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Duración del objeto está disponible cuando la opción **Recopilar también la información de duración de los objetos .NET** está activada en las páginas de propiedades de la sesión de rendimiento.  
  
 El recolector de elementos no utilizados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] administra la asignación y liberación de la memoria de la aplicación.  Para optimizar el rendimiento del recolector de elementos no utilizados, el montón administrado se divide en tres generaciones: 0, 1 y 2.  El recolector de elementos no utilizados del runtime almacena los nuevos objetos en la generación 0.  Los objetos que sobreviven a las recolecciones se promueven y se almacenan en las generaciones 1 y 2.  
  
 El recolector de elementos no utilizados recupera memoria desasignando una generación completa de objetos.  Para los objetos creados por la aplicación para la que se generan perfiles, la vista Duración del objeto muestra el número y el tamaño de los objetos, así como la generación en la que se recuperan.  
  
## General  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Nombre de clase**|Nombre de clase del tipo asignado.|  
|**Id. de proceso**|Identificador de proceso de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
  
## Datos de instancia  
 Los datos de instancia indican el número de objetos del tipo que se crearon en la generación de perfiles, así como la generación en la que el recolector de elementos no utilizados desasignó los objetos.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Instancias**|Número de asignaciones de objetos de este tipo.|  
|**Total de instancias %**|Porcentaje del número total de asignaciones realizadas durante la generación de perfiles.|  
|**Instancias recopiladas en la generación 0**|Número de instancias del tipo que se desasignaron en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 1**|Número de instancias del tipo que se desasignaron en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 2**|Número de instancias del tipo que se desasignaron en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias activas al final**|Número de instancias del tipo que no se desasignaron hasta el final de la generación de perfiles.|  
  
## Datos de tamaño \(bytes\)  
 Los datos de tamaño \(bytes\) indican el tamaño de los objetos del tipo que se crearon en la generación de perfiles y la cantidad de memoria que se reclamó en cada generación en la que se desasignaron los objetos.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Bytes totales asignados**|Número total de bytes para todas las instancias del tipo.|  
|**Total de bytes %**|Porcentaje del número total de bytes asignados en la generación de perfiles que se asignaron para las instancias de este tipo.|  
|**Bytes recopilados en la generación 0**|Tamaño de las instancias del tipo que se desasignaron en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 1**|Tamaño de las instancias del tipo que se desasignaron en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 2**|Tamaño de las instancias del tipo que se desasignaron en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
  
## Datos del montón de objetos grandes  
 El asignador de memoria de .NET administra objetos muy grandes en una ubicación que es independiente del montón administrado estándar.  Los datos del montón de objetos grandes indican el número y el tamaño de los objetos del tipo que se administraron en esta ubicación.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Instancias recopiladas de montón de objetos grandes**|Número de las instancias de este tipo que se ubicaron en el montón de objetos grandes y que se recopilaron en la generación de perfiles.|  
|**Bytes recopilados de montón de objetos grandes**|Tamaño, en bytes, de las instancias de este tipo que se ubicaron en el montón de objetos grandes y que se recopilaron en la generación de perfiles.|  
  
## Vea también  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)