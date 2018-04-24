---
title: 'Vista Líneas: datos de contención | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b01c8aa176fe92cb4309990693063dcd27cf15a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="lines-view---contention-data"></a>Vista Líneas: datos de contención
La vista Líneas de datos de contención muestra los datos de rendimiento de las instrucciones que se estaban ejecutando cuando se recopilaron las muestras en la ejecución de generación de perfiles. En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción.  
  
 Una instrucción se identifica mediante los siguientes datos:  
  
-   El archivo de código fuente que contiene la instrucción de la función.  
  
-   La función que contiene la instrucción.  
  
-   La línea de origen donde se inicia la instrucción.  
  
-   El carácter en la línea de origen donde se inicia la instrucción.  
  
-   La línea de origen donde finaliza la instrucción.  
  
-   El carácter en la línea de origen donde finaliza la instrucción.  
  
 La columna Nombre de línea proporciona una concatenación ordenable de datos del identificador.  
  
 En la siguiente tabla se describen las columnas del informe de vista de líneas.  
  
|Columna|Description|  
|------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|La cantidad de tiempo durante el cual esta instrucción no pudo ejecutar el código de la instrucción debido a un evento de contención. No se incluye el tiempo de bloqueo de las funciones a las que llamó la instrucción.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|El porcentaje de tiempo de bloqueo total en el proceso que es tiempo de bloqueo exclusivo de la instrucción.|  
|**Contenciones exclusivas**|El número de veces que esta instrucción no pudo ejecutar el código de la instrucción debido a un evento de contención. No se incluyen los eventos de contención de las funciones a las que llamó la instrucción.|  
|**Porcentaje de contenciones exclusivas**|El porcentaje de todos los eventos de contención en el proceso que eran contenciones exclusivas de esta instrucción.|  
|**Dirección de la función**|La dirección de la función que contiene esta instrucción.|  
|**Nombre de la función**|El nombre completo de la función que contiene esta instrucción.|  
|**Tiempo de bloqueo inclusivo**|El tiempo bloqueado en esta instrucción y las funciones a las que llama la instrucción.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|El porcentaje de tiempo de bloqueo total en el proceso que es tiempo de bloqueo inclusivo de la instrucción.|  
|**Contenciones inclusivas**|El número de veces que se bloqueó la ejecución de esta instrucción y las funciones a las que llamó la instrucción.|  
|**Porcentaje de contenciones inclusivas**|El porcentaje de todos los eventos de contención en el proceso que eran contenciones inclusivas de esta instrucción.|  
|**Nombre de línea**|Un identificador generado por el generador de perfiles de la línea. El identificador utiliza la siguiente sintaxis:`SourceFile`**;[**`LineNumberStart`**,**`CharacterStart`**]->;[**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la instrucción.|  
|**Identificador de proceso**|El identificador de proceso (PID) del proceso del que se generaron perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se inicia la instrucción.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde finaliza la instrucción.|  
|**Archivo de código fuente**|El nombre del archivo de código fuente que contiene la instrucción de la función.|  
|**Línea de inicio del origen**|El número de línea en el archivo de origen en el que comienza esta instrucción.|  
|**Línea de finalización del origen**|El número de línea en el archivo de origen en el que finaliza esta instrucción.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Líneas](../profiling/lines-view.md)   
 [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Vista Líneas](../profiling/lines-view-sampling-data.md)