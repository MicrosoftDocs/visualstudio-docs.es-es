---
title: 'Vista Módulos: datos de muestreo de memoria de .NET | Microsoft Docs'
description: Obtenga información sobre la vista Módulos de los datos de asignación de memoria de .NET que se recopilan mediante el método de muestreo.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: b9c00fd7647d6ba3da62d913e0371dc8cf300ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879831"
---
# <a name="modules-view---net-memory-sampling-data"></a>Vista Módulos: datos de muestreo de memoria de .NET
La vista Módulos de los datos de asignación de memoria de .NET recopilados con el método de muestro agrupa los datos de memoria por los módulos que se ejecutaron durante la generación de perfiles. Cada módulo es la raíz de un árbol jerárquico. Las funciones del módulo se enumeran bajo el nodo de módulo.

 Los números de línea del archivo de origen de las instrucciones que asignan memoria se enumeran bajo el nodo de función y las direcciones de las instrucciones que realizan la asignación se enumeran bajo el nodo de línea. Los valores inclusivos y exclusivos siempre son los mismos para los datos de línea y de instrucción.

|Columna|Descripción|
|------------|-----------------|
|**Nombre**|El nombre del módulo, función, número de línea o dirección de instrucción.|
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|
|**Nombre del proceso**|Nombre del proceso.|
|**Nombre del módulo**|Nombre del módulo que contiene la función.|
|**Ruta de acceso del módulo**|La ruta de acceso del módulo.|
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|
|**Asignaciones inclusivas**|-   Para una función, el número total de objetos creados por la función. El número incluye los objetos creados en las funciones llamadas por esta función.<br />-   Para un módulo, el número de objetos en una generación de perfiles asignados mientras se estaba ejecutando al menos una función del módulo. El número incluye los objetos creados en las funciones llamadas por las funciones del módulo.<br />-   Para una línea o instrucción, el número total de objetos asignados por la línea o instrucción.|
|**Porcentaje de asignaciones inclusivas**|El porcentaje de todos los objetos que se asignaron durante la generación de perfiles que son asignaciones inclusivas del módulo, función, línea o instrucción.|
|**Asignaciones exclusivas**|-   En la función actual, el número de objetos creados cuando la función estaba ejecutando código del cuerpo de la función (es decir, cuando la función estaba en la parte superior de la pila de llamadas). El número no incluye los objetos creados en las funciones a las que llamó esta función.<br />-   Para un módulo, la suma de las asignaciones exclusivas de las funciones del módulo.<br />-   Para una línea o instrucción, el número total de objetos creadas por esta línea o instrucción.|
|**Porcentaje de asignaciones exclusivas**|El porcentaje de todos los objetos que se asignaron durante la generación de perfiles que son asignaciones exclusivas del módulo, función, línea o instrucción.|
|**Porcentaje de bytes inclusivos**|-   Para una función, el número de bytes asignados por la función. El número incluye los bytes asignados en las funciones llamadas por esta función.<br />-   Para un módulo, el número de bytes asignados en una generación de perfiles que se asignaron mientras se estaba ejecutando al menos una función del módulo. El número incluye los objetos creados en todas las funciones llamadas por las funciones del módulo.<br />-   Para una línea o instrucción, el número total de objetos creadas por la línea o instrucción.|
|**Porcentaje de bytes inclusivos**|El porcentaje de todos los bytes que se asignaron durante la generación de perfiles que son bytes inclusivos del módulo, función, línea o instrucción.|
|**Bytes exclusivos**|-   Para una función, el número total de bytes asignados por la función. El número no incluye los bytes asignados en las funciones llamadas por esta función.<br />-   Para un módulo, la suma de bytes exclusivos que fueron asignados por las funciones del módulo.<br />-   Para una línea o instrucción, el número total de objetos asignados por esta línea o instrucción.|
|**Porcentaje de bytes exclusivos**|El porcentaje de todos los bytes que se asignaron durante la generación de perfiles que son bytes exclusivos del módulo, función, línea o instrucción.|

## <a name="see-also"></a>Consulte también
- [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)
- [Vista Módulos: instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Vista Módulos](../profiling/modules-view-sampling-data.md)
- [Vista Módulos](../profiling/modules-view-instrumentation-data.md)
