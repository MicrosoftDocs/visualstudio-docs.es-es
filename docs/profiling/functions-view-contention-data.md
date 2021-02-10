---
title: 'Vista Funciones: datos de contención | Microsoft Docs'
description: Obtenga información sobre la vista de datos de contención del informe Funciones, que enumera las funciones en la ejecución de la generación de perfiles que no se han podido ejecutar durante la ejecución de la generación de perfiles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6392263e7e30790ff09340bffebed8f921e24765
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907416"
---
# <a name="functions-view---contention-data"></a>Vista Funciones: datos de contención
La vista de informe Funciones de datos de contención enumera las funciones en la ejecución de generación de perfiles a las que se les ha impedido la ejecución durante la ejecución de generación de perfiles.

 En la tabla siguiente, se explican los valores que se muestran en la vista Funciones de un archivo de datos de generación de perfiles recopilado con el método de simultaneidad.

|Columna|Descripción|
|------------|-----------------|
|**Tiempo de bloqueo exclusivo**|Tiempo durante el cual esta función no pudo ejecutar código en el cuerpo de la función. No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|
|**Porcentaje de tiempo de bloqueo exclusivo**|Porcentaje de tiempo de bloqueo exclusivo de esta función con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|
|**Contenciones exclusivas**|Número de veces en las que esta función no pudo ejecutar código en el cuerpo de la función. No se incluyen las contenciones en las funciones a las que ha llamado la función.|
|**Porcentaje de contenciones exclusivas**|Porcentaje de contenciones exclusivas de esta función con respecto a todas las contenciones en la ejecución de generación de perfiles.|
|**Dirección de función**|Dirección de la función.|
|**Nombre de la función**|El nombre completo de la función.|
|**Tiempo de bloqueo inclusivo**|Tiempo durante el cual esta función o una función llamada por esta función no pudieron ejecutarse.|
|**Porcentaje de tiempo de bloqueo inclusivo**|Porcentaje de tiempo de bloqueo inclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|
|**Contenciones inclusivas**|Número de veces que esta función o una función llamada por esta función no pudieron ejecutarse.|
|**Porcentaje de contenciones inclusivas**|Porcentaje de contenciones inclusivas de esta función o módulo con respecto a todas las contenciones en la ejecución de generación de perfiles.|
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|
|**Nombre del módulo**|Nombre del módulo que contiene la función.|
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|
|**Identificador del proceso**|El Id. del proceso (PID) en el que se estaba ejecutando la función.|
|**Nombre del proceso**|Nombre del proceso.|
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|

## <a name="see-also"></a>Vea también
- [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)
- [Vista Funciones](../profiling/functions-view.md)
- [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Vista Funciones](../profiling/functions-view-instrumentation-data.md)
- [Vista Funciones](../profiling/functions-view-sampling-data.md)
