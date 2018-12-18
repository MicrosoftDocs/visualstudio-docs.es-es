---
title: 'Vista Árbol de llamadas: datos de instrumentación de memoria de .NET | Microsoft Docs'
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
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed87363751c18794d9cf4c00e156d75760e0bf8d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782510"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Vista Árbol de llamadas: datos de instrumentación de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la vista Árbol de llamadas de los datos de generación de perfiles de asignación de memoria de .NET recopilados con el método de instrumentación se muestran las rutas de acceso de ejecución de función que se recorrieron en la aplicación en la que se generaron perfiles. La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función muestra todas las funciones a las que llamó, así como los datos de tiempo y de memoria de .NET de dicha función.  
  
 Los valores en la vista Árbol de llamadas se refieren a las instancias de la función a las que llamó la función primaria en el árbol de llamadas. Los valores de porcentaje se calculan mediante la comparación del valor de instancia de función con el tamaño o número total de asignaciones de la ejecución de asignación de perfiles.  
  
## <a name="highlighting-the-execution-hot-path"></a>Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas puede expandir y resaltar la ruta de acceso de ejecución del proceso o la función que creó la mayoría de los objetos de memoria, o los más grandes. Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## <a name="setting-the-call-tree-root-node"></a>Establecer el nodo raíz del árbol de llamadas  
 Cada proceso en la ejecución de generación de perfiles se muestra como un nodo raíz. Para establecer el nodo inicial de la vista Árbol de llamadas, haga clic con el botón derecho en el nodo que quiere establecer como nodo de inicio y seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado. Puede restablecer el nodo raíz en el nodo que estaba viendo. Para ello, haga clic con el botón derecho en la ventana de la vista Árbol de llamadas y seleccione **Restablecer raíz**.  
  
## <a name="general"></a>General  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de la función**|Dirección de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|El número total de llamadas realizadas a esta función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|El nombre que se asigna al proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Type**|El contexto de la función:<br /><br /> -   **0**: la función actual<br />-   **1**: una función que llama a la función actual<br />-   **2**: una función llamada por la función actual<br /><br /> Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-values"></a>Valores de memoria de .NET  
 Los valores de memoria de .NET inclusivos de una función indican el número (asignaciones) y el tamaño (bytes) de los objetos creados por la función y las funciones llamadas por dicha función.  
  
 Los valores de memoria exclusivos indican el número y el tamaño de los objetos creados mediante código en el cuerpo de la función, y no por las funciones llamadas por dicha función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Asignaciones inclusivas**|Número de objetos asignados por las instancias de esta función a las que llamó la función primaria del árbol de llamadas. Este número incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de objetos creados en la ejecución de generación de perfiles que eran asignaciones inclusivas de las instancias de la función llamadas por la función primaria del árbol de llamadas.|  
|**Asignaciones exclusivas**|Número de objetos asignados por las instancias de esta función a las que llamó la función primaria del árbol de llamadas. Este número no incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de objetos creados en la ejecución de generación de perfiles que eran asignaciones exclusivas de las instancias de la función llamadas por la función primaria del árbol de llamadas.|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones a las que llamó la función y a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|El tiempo inclusivo total transcurrido de todas las llamadas a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo total transcurrido de esta función cuando la llamó la función primaria del árbol de llamadas.|  
|**Promedio de tiempo inclusivo transcurrido**|El tiempo inclusivo medio transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo inclusivo máximo transcurrido**|El tiempo inclusivo máximo transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo inclusivo transcurrido mínimo**|El tiempo inclusivo mínimo transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. El tiempo también incluye el tiempo dedicado a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S. Sin embargo, el tiempo no incluye el tiempo dedicado a las funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|El tiempo exclusivo total transcurrido de todas las llamadas a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo total transcurrido de esta función cuando la llamó la función primaria del árbol de llamadas.|  
|**Promedio de tiempo exclusivo transcurrido**|El tiempo exclusivo medio transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo exclusivo transcurrido máximo**|El tiempo exclusivo máximo transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo exclusivo mínimo transcurrido**|El tiempo exclusivo mínimo transcurrido de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de E/S. El tiempo incluye el tiempo dedicado a funciones secundarias a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función cuando fue llamada por la función primaria del árbol de llamadas.|  
|**Promedio de tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación medio de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo inclusivo máximo de aplicación**|El tiempo inclusivo de aplicación máximo de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo inclusivo mínimo de aplicación**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo dedicado a la función, excluido el tiempo dedicado a funciones secundarias llamadas por dicha función. El tiempo también excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función cuando fue llamada por la función primaria del árbol de llamadas.|  
|**Promedio de tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación medio de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Tiempo exclusivo mínimo de aplicación**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función cuando la llamó la función primaria en el árbol de llamadas.|



