---
title: 'Vista Proceso: datos de contención | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46bd3506744d37d3f203215cd9c152cef20142f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776686"
---
# <a name="process-view---contention-data"></a>Vista Proceso: datos de contención
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Proceso muestra datos de contención de los procesos y subprocesos que se ejecutaron durante la generación de perfiles.  
  
 Cuando haya símbolos disponibles, los procesos se enumeran por nombre. Cuando no haya símbolos disponibles, los procesos se enumeran por su dirección de memoria en formato hexadecimal. Los subprocesos se enumeran como elementos secundarios del proceso que los creó.  
  
 En la siguiente tabla se explican los valores de las columnas de la tabla de vista Proceso.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Hora de inicio**|El número de milisegundos o ciclos de procesador desde el inicio de la generación de perfiles hasta el inicio del proceso o subproceso.|  
|**Tiempo de bloqueo**|El tiempo total durante el cual no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**Porcentaje de tiempo de bloqueo**|El porcentaje de la duración del proceso o subproceso en el que no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**Contenciones**|El número de veces que no se pudieron ejecutar las funciones del proceso o subproceso.|  
|**Porcentaje de contenciones**|El porcentaje de todas las contenciones de la generación de perfiles que son contenciones del proceso o subproceso.|  
|**Hora de finalización**|El número de milisegundos o ciclos de procesador desde el inicio de la generación de perfiles hasta el final del proceso o subproceso.|  
|**ID**|El identificador generado por el sistema del proceso o subproceso.|  
|**Duración**|El número de milisegundos o ciclos de procesador desde el inicio del proceso o subproceso hasta el final del proceso o subproceso o el final de la generación de perfiles.|  
|**ype**|El tipo de fila, ya sea un proceso o un subproceso.<br /><br /> Solo disponible en los informes de línea de comandos de **VSReport**. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|El nombre del proceso o subproceso.|  
|**Id. único**|Un identificador generado por el generador de perfiles que es único para el proceso o subproceso.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Proceso](../profiling/process-view.md)



