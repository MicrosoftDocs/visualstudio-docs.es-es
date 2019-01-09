---
title: Vista Detalles de la función | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ba470b4ec9ef3bc52f9c7250649fc098c999149
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945345"
---
# <a name="function-details-view"></a>Vista Detalles de la función
La ventana de **Vista Detalles de la función** muestra la siguiente información:  
  
- El gráfico de barras **Distribución del costo** representa las relaciones entre la función seleccionada y las funciones de llamada que la han ejecutado. También indica las relaciones entre la función seleccionada y aquellas a las que llamó.  
  
- La tabla **Detalles de rendimiento de la función**, que muestra de manera resumida los datos de generación de perfiles para la función que especifique.  
  
- La ventana **Vista de código de función**, que muestra el código de función cuando el código está disponible.  
  
  La ventana **Vista de código de función** es un panel independiente. De forma predeterminada, los dos paneles se dividen horizontalmente y la ventana **Vista de código de función** ocupa la parte inferior del marco.  
  
- Para dividir los dos paneles verticalmente, haga clic en **Dividir la pantalla verticalmente** en la barra de herramientas.  
  
- Para cambiar el tamaño relativo de los paneles, haga clic en el borde sombreado entre los marcos y arrastre el borde a una ubicación diferente.  
  
## <a name="cost-distribution-bar-chart"></a>Gráfico de barras de distribución del costo  
  
### <a name="performance-metrics"></a>Métricas de rendimiento  
 En la lista desplegable **Métrica de rendimiento**, puede especificar los valores que aparecen en la vista. Los valores que están disponibles dependen del método de generación de perfiles que se utilizó en el archivo de datos de generación de perfiles. Los nombres entre paréntesis son nombres de filas de la tabla **Detalles de rendimiento de la función**.  
  
### <a name="bar-chart"></a>Gráfico de barras  
 **Funciones de llamada**  
  
 La barra **Funciones de llamada** muestra las funciones que llamaron a la función seleccionada. El tamaño del bloque que contiene la función de llamada es proporcional a la contribución de la función de llamada al valor total de la métrica de rendimiento para la función seleccionada.  
  
 Puede hacer clic en el nombre de una función de llamada para convertirla en la función seleccionada en la vista.  
  
- Si hay demasiadas funciones de llamada para mostrar en la lista, las funciones con las contribuciones más pequeñas se recopilan en el bloque **Otros**. Haga clic en **Otros** para ver todas las funciones llamadas y de llamada de la función seleccionada en la ventana de la **vista Llamador y destinatario**. Para obtener más información, consulte [Vista Llamador y destinatario](../profiling/caller-callee-view.md).  
  
- Si no hay funciones de llamada o si la función es la función de entrada de un subproceso o un proceso, aparece un bloque **Parte superior de la pila**.  
  
  **Función seleccionada**  
  
  La barra de función seleccionada muestra las contribuciones de las funciones llamadas y del código de la función seleccionada a la métrica de rendimiento total de la función seleccionada. El tamaño del bloque que contiene una función llamada o el cuerpo de la función es proporcional a su contribución al valor total de la métrica de rendimiento para la función seleccionada.  
  
  Puede hacer clic en el nombre de una función llamada para convertirla en la función seleccionada en la vista.  
  
- El valor **Total** es la métrica de rendimiento para la función seleccionada.  
  
- El bloque **Cuerpo de la función** representa la cantidad del valor total de la métrica de rendimiento que se produjo en la ejecución directa del código en el cuerpo de la función.  
  
- Las funciones a las que llamó la función seleccionada se muestran en bloques. El tamaño del bloque de las funciones seleccionadas representa la cantidad de la métrica de rendimiento total para la función seleccionada que se produjo en la función llamada.  
  
- Si hay demasiadas funciones de llamada para mostrar en la lista, las funciones con las contribuciones más pequeñas se recopilan en el bloque **Otros**. Haga clic en **Otros** para ver todas las funciones llamadas y de llamada de la función seleccionada en la ventana de la **vista Llamador y destinatario**. Para obtener más información, consulte [Vista Llamador y destinatario](../profiling/caller-callee-view.md).  
  
- Si no hay funciones llamadas, aparece un bloque **Parte inferior de la pila**.  
  
## <a name="function-performance-details"></a>Detalles de rendimiento de la función  
 La tabla Detalles de rendimiento de la función proporciona datos de resumen de las métricas de rendimiento de la función seleccionada. Aparecen el valor y el porcentaje. Se especifican los datos de generación de perfiles que aparecen en el gráfico y la tabla de detalles en la lista **Métrica de rendimiento**.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Exclusivo**|- La cantidad de la métrica de rendimiento que se produjo en la ejecución del cuerpo de la función.|  
|**Llamadas entrantes**|- La cantidad de la métrica de rendimiento que se produjo en las funciones a las que llamó la función seleccionada.|  
|**Total inclusivo**|- El total de los valores **Exclusivo** y **Llamadas entrantes**.|  
  
## <a name="function-code-view"></a>Vista de código de función  
 La ventana **Vista de código de función** muestra una lista del código fuente cuando está disponible. Una columna sombreada, situada junto a las líneas de código fuente que llaman a otras funciones, contiene los valores de métrica de rendimiento de la función llamada. Para editar el código fuente, haga clic en el vínculo al archivo de código fuente.  
  
## <a name="cost-distribution-bar-chart-values"></a>Valores del gráfico de barras Distribución del costo  
  
### <a name="sampling"></a>Muestreo  
 En la tabla siguiente se explican los valores de la lista Métrica de rendimiento para los datos de generación de perfiles recopilados con el método de muestreo.  
  
|||  
|-|-|  
|**Muestras inclusivas (muestras recopiladas)**|- En una función de llamada, el número de muestras recopiladas cuando esta función llamó a la función seleccionada.<br />- En el cuerpo de la función, el número de muestras recopiladas cuando la función seleccionada estaba ejecutando su propio código.<br />- En una función llamada, el número de muestras recopiladas cuando se estaba ejecutando la función llamada debido a una llamada de la función seleccionada.|  
  
### <a name="instrumentation"></a>Instrumentación  
 En la tabla siguiente se explican los valores de la lista Métrica de rendimiento para los datos de generación de perfiles recopilados con el método de instrumentación.  
  
|||  
|-|-|  
|**Tiempo inclusivo transcurrido (tiempo transcurrido)**|El tiempo transcurrido incluye el tiempo dedicado a llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada/salida.<br /><br /> - En una **Función de llamada**, la cantidad de tiempo transcurrido dedicado a ejecutar las instancias de la función seleccionada a las que llamó la función. Se incluye el tiempo dedicado a las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, la cantidad total de tiempo transcurrido dedicado a ejecutar el código de la función seleccionada. No se incluye el tiempo dedicado a las funciones llamadas.<br />- En una función llamada, la cantidad de tiempo dedicado a ejecutar las instancias de la función a las que llamó la función seleccionada. El total incluye el tiempo dedicado a funciones a las que llamó la función. Se incluye el tiempo dedicado a las funciones a las que llamó la función seleccionada.|  
|**Tiempo inclusivo de aplicación (tiempo de aplicación)**|El tiempo de aplicación no incluye el tiempo dedicado a llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada/salida.<br /><br /> - En una **Función de llamada**, la cantidad de tiempo de aplicación dedicado a ejecutar las instancias de la función seleccionada a las que llamó la función. Se incluye el tiempo dedicado a las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, la cantidad total de tiempo de aplicación dedicado a ejecutar el código de la función seleccionada. No se incluye el tiempo dedicado a las funciones llamadas.<br />- En una función llamada, la cantidad de tiempo de aplicación dedicado a ejecutar las instancias de la función a las que llamó la función seleccionada. El total incluye el tiempo dedicado a funciones a las que llamó la función.|  
  
### <a name="net-memory"></a>Memoria de .NET  
 En la tabla siguiente se explican los valores de la lista Métrica de rendimiento para los datos de generación de perfiles recopilados con el método de generación de perfiles de memoria de .NET.  
  
|||  
|-|-|  
|**Asignaciones inclusivas (asignaciones)**|- En una **Función de llamada**, el número de objetos asignados por las instancias de la función seleccionada a las que llamó la función. El número incluye los objetos asignados por las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, el número de objetos que asignó la función seleccionada cuando estaba ejecutando su propio código. No se incluyen los objetos asignados en funciones a las que llamó la función seleccionada.<br />- En una función llamada, el número de objetos asignados por las instancias de la función a las que llamó la función seleccionada. El número incluye los objetos asignados por las funciones a las que llamó la función.|  
|**Bytes inclusivos (bytes)**|- En una **Función de llamada**, el número de bytes asignados por las instancias de la función seleccionada a las que llamó la función. El número incluye los bytes asignados por las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, el número total de bytes que asignó la función seleccionada cuando estaba ejecutando su propio código. No se incluyen los bytes asignados en funciones a las que llamó la función seleccionada.<br />- En una función llamada, el número de bytes asignados por las instancias de la función a las que llamó la función seleccionada. El número incluye los bytes asignados por las funciones a las que llamó la función.|  
  
### <a name="concurrency"></a>Simultaneidad  
 En la tabla siguiente se explican los valores de la lista Métrica de rendimiento para los datos de generación de perfiles recopilados con el método de simultaneidad.  
  
|||  
|-|-|  
|**Contenciones inclusivas (contenciones)**|- En una **Función de llamada**, el número de eventos de contención de recursos que se produjeron en las instancias de la función seleccionada a las que llamó la función. El número incluye los eventos de contención de las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, el número total de eventos de contención que se produjeron cuando la función estaba ejecutando su propio código. No se incluyen las contenciones que se produjeron en funciones a las que llamó la función seleccionada.<br />- En una función llamada, el número de eventos de contención que se produjeron en las instancias de la función a la que llamó la función seleccionada. El número incluye los eventos de contención que se produjeron en las funciones a las que llamó la función.|  
|**Tiempo de bloqueo inclusivo (tiempo de bloqueo)**|- En una función de llamada, el tiempo dedicado a los eventos de contención de recursos de las instancias de la función seleccionada a las que llamó la función. Se incluye el tiempo de bloqueo de las funciones a las que llamó la función seleccionada.<br />- En el **Cuerpo de función**, el tiempo total dedicado a los eventos de contención que se produjeron cuando la función estaba ejecutando su propio código. No se incluyen las contenciones que se produjeron en funciones a las que llamó la función seleccionada.<br />- En una función llamada, el tiempo dedicado a los eventos de contención de recursos de las instancias de la función a la que llamó la función seleccionada. Se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|