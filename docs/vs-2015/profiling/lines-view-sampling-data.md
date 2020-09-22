---
title: 'Vista Líneas: datos de muestreo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2e5511e9e2e1c863db8f696a70195573d75429f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843249"
---
# <a name="lines-view---sampling-data"></a>Vista Líneas: datos de muestreo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Líneas de datos de muestreo muestra los datos de rendimiento de las instrucciones que se estaban ejecutando cuando se recopilaron las muestras en la ejecución de generación de perfiles.  
  
> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción. Una instrucción se identifica mediante lo siguiente:  
  
- El archivo de código fuente que contiene la instrucción de la función.  
  
- La función que contiene la instrucción.  
  
- La línea de origen donde comienza la instrucción.  
  
- El carácter en la línea de origen donde se inicia la instrucción.  
  
- La línea de origen donde finaliza la instrucción.  
  
- El carácter en la línea de origen donde finaliza la instrucción.  
  
  La columna Nombre de línea proporciona una concatenación ordenable de datos del identificador.  
  
  Por definición, una instrucción no llama a otras funciones. Por lo tanto, se muestran solo los valores exclusivos.  
  
|Columna|Description|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la línea de función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la línea de función.|  
|**Archivo de origen**|El archivo de código fuente que contiene la línea de la función.|  
|**Nombre de la función**|Nombre de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|La dirección de inicio de la función.|  
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se recopiló esta muestra.|  
|**Línea de finalización del origen**|Número de la línea de finalización del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Nombre de línea**|Un identificador generado por el generador de perfiles de la línea con la siguiente sintaxis:`Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number End` **,** `Character End` **]**|  
|**Muestras exclusivas**|El número total de muestras recopiladas cuando la línea de la función se estaba ejecutando.|  
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras que se recopilaron durante la generación de perfiles mientras se ejecutaba la línea de la función.|  
  
## <a name="see-also"></a>Consulte también  
 [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)
