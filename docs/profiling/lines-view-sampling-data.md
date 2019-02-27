---
title: 'Vista Líneas: datos de muestreo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0f527d6f12d841175afbaff0e653b817250cb4c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625184"
---
# <a name="lines-view---sampling-data"></a>Vista Líneas: datos de muestreo
La vista Líneas de datos de muestreo muestra los datos de rendimiento de las instrucciones que se estaban ejecutando cuando se recopilaron las muestras en la ejecución de generación de perfiles.

> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción. Una instrucción se identifica mediante lo siguiente:

- El archivo de código fuente que contiene la instrucción de la función.

- La función que contiene la instrucción.

- La línea de origen donde comienza la instrucción.

- El carácter en la línea de origen donde se inicia la instrucción.

- La línea de origen donde finaliza la instrucción.

- El carácter en la línea de origen donde finaliza la instrucción.

  La columna Nombre de línea proporciona una concatenación ordenable de datos del identificador.

  Por definición, una instrucción no llama a otras funciones. Por lo tanto, se muestran solo los valores exclusivos.

|Columna|Descripción|
|------------|-----------------|
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|
|**Nombre de proceso**|Nombre del proceso.|
|**Nombre del módulo**|Nombre del módulo que contiene la línea de función.|
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la línea de función.|
|**Archivo de código fuente**|El archivo de código fuente que contiene la línea de la función.|
|**Nombre de la función**|Nombre de la función.|
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|
|**Dirección de la función**|La dirección de inicio de la función.|
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se recopiló esta muestra.|
|**Línea de finalización del origen**|Número de la línea de finalización del archivo de origen donde se recopiló esta muestra.|
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se recopiló esta muestra.|
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se recopiló esta muestra.|
|**Nombre de línea**|Un identificador generado por el generador de perfiles de la línea con la siguiente sintaxis:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number End`**,**`Character End`**]**|
|**Muestras exclusivas**|El número total de muestras recopiladas cuando la línea de la función se estaba ejecutando.|
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras que se recopilaron durante la generación de perfiles mientras se ejecutaba la línea de la función.|

## <a name="see-also"></a>Vea también
- [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)