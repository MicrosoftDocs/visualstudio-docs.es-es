---
title: "Vista Proceso: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Proceso (vista)"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Proceso: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Proceso muestra los datos de contención de los procesos y subprocesos que se ejecutaron durante la generación de perfiles.  
  
 Cuando hay símbolos disponibles, los procesos se enumeran por nombre.  Si no hay símbolos disponibles, los procesos se enumeran por su dirección de memoria, en formato hexadecimal.  Los subprocesos se enumeran como elementos secundarios del proceso que los creó.  
  
 En la tabla siguiente se explican los valores de las columnas de la tabla de la vista Proceso.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Hora de inicio**|Número de milisegundos o ciclos de procesador desde el inicio de la generación de perfiles hasta el inicio del proceso o subproceso.|  
|**Tiempo de bloqueo**|Tiempo total durante el cual no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**% de tiempo de bloqueo**|Porcentaje de la duración del proceso o subproceso en que no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**Contenciones**|Número de veces que no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**% de contenciones**|Porcentaje de contenciones del proceso o subproceso con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Hora de finalización**|Número de milisegundos o ciclos de procesador desde el inicio de la generación de perfiles hasta el final del proceso o subproceso.|  
|**ID**|Identificador generado por el sistema del proceso o subproceso.|  
|**Duración**|Número de milisegundos o ciclos de procesador desde el inicio del proceso o subproceso hasta el final del proceso o subproceso o hasta el final de la generación de perfiles.|  
|**Tipo**|Tipo de fila, ya sea proceso o subproceso.<br /><br /> Solo en informes de línea de comandos de **VSReport**.  Para obtener más información, vea [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|Nombre del proceso o subproceso.|  
|**Identificador único**|Identificador generado por el generador de perfiles que es único en el proceso o subproceso.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Proceso](../profiling/process-view.md)