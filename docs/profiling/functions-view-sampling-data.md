---
title: 'Vista Funciones: datos de muestreo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 70fda712a29ff07ee34a4ac76a06198cb5ead8a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780031"
---
# <a name="functions-view---sampling-data"></a>Vista Funciones: datos de muestreo
La vista de informe de funciones para el método de perfiles de muestreo enumera las funciones que se muestrearon durante la ejecución de generación de perfiles.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Columna|Descripción|
|------------|-----------------|
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|
|**Nombre de proceso**|Nombre del proceso.|
|**Nombre del módulo**|Nombre del módulo que contiene la función.|
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|
|**Nombre de la función**|El nombre completo de la función.|
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|
|**Dirección de la función**|Dirección de la función.|
|**Muestras inclusivas**|El número total de muestras recopiladas cuando se estaba ejecutando esta función; es decir, el número de muestras recopiladas cuando esta función estaba en la pila de llamadas. El número incluye las muestras recopiladas cuando se ejecutaban funciones a las que llamó esta función.|
|**Porcentaje de muestras inclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que fueron muestras inclusivas de esta función.|
|**Muestras exclusivas**|El número total de muestras recopiladas cuando se estaba ejecutando código en el cuerpo de esta función; es decir, cuando esta función estaba en la parte superior de la pila de llamadas. Las muestras recopiladas en funciones a las que llamó esta función no se incluyen.|
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que fueron muestras exclusivas de esta función.|

## <a name="see-also"></a>Vea también
- [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)
- [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Vista Funciones](../profiling/functions-view-instrumentation-data.md)
