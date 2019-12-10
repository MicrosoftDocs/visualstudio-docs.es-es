---
title: Descripción de los métodos de recopilación de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ad451c6146593713b02901ac43423c76174d0684
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778094"
---
# <a name="understand-performance-collection-methods"></a>Descripción de los métodos de recopilación de rendimiento

Las Herramientas de generación de perfiles de Visual Studio proporcionan cinco métodos para recopilar datos de rendimiento. En este tema se describen los distintos métodos y se sugieren algunos escenarios en los que puede resultar apropiado recopilar datos con un método determinado.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Método|DESCRIPCIÓN|
|------------|-----------------|
|[Muestreo](#sampling)|Recopila datos estadísticos sobre el trabajo realizado por una aplicación.|
|[Instrumentación](#instrumentation)|Recopila información de tiempo detallada sobre cada llamada a una función.|
|[Simultaneidad](#concurrency)|Recopila información detallada sobre las aplicaciones multiproceso.|
|[Memoria de .NET](#net-memory)|Recopila información detallada sobre la asignación de memoria de .NET y la recolección de elementos no utilizados.|
|[Interacción de capas](#tier-interaction)|Recopila información sobre las llamadas de funciones ADO.NET sincrónicas a una base de datos de SQL Server.<br /><br /> La generación de perfiles de interacción de capas se puede recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.|

Con algunos de los métodos de generación de perfiles también es posible recopilar datos adicionales, como contadores de rendimiento del software y el hardware. Para obtener más información, consulte [Recopilación de datos de rendimiento adicionales](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Muestreo

El método de generación de perfiles de muestreo recopila datos estadísticos sobre el trabajo realizado por una aplicación durante una generación de perfiles. El método de muestreo consume pocos recursos y afecta poco a la ejecución de los métodos de la aplicación.

El muestreo es el método predeterminado de las Herramientas de generación de perfiles de Visual Studio. Es útil para lo siguiente:

- Exploraciones iniciales del rendimiento de la aplicación.
- Investigación de problemas de rendimiento que implican la utilización del procesador (CPU).

El método de generación de perfiles de muestreo interrumpe el procesador del equipo a intervalos establecidos y recopila la pila de llamadas a función. Los recuentos de muestras exclusivos se incrementan para la función que se está ejecutando, mientras que los recuentos inclusivos se incrementan para todas las funciones de llamada de la pila de llamadas. Los informes de muestreo presentan los totales de estos recuentos para el módulo, la función, la línea de código fuente y la instrucción cuyos perfiles se están generando.

De forma predeterminada, el generador de perfiles establece el intervalo de muestreo en los ciclos de la CPU. Puede cambiar el tipo de intervalo a otro contador de rendimiento de la CPU y establecer el número de eventos de contador del intervalo. También puede recopilar datos de generación de perfiles de interacción de capa (TIP) que proporcionen información sobre las consultas realizadas a una base de datos de SQL Server a través de ADO.NET.

[Recopilación de estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)

[Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentación

El método de generación de perfiles de instrumentación recopila información de tiempo detallada de las llamadas a funciones en una aplicación cuyos perfiles se están generando. La generación de perfiles de instrumentación es útil para:

- Investigación de cuellos de botella de entrada o salida, como E/S de disco.
- Examen exhaustivo de un módulo determinado o un conjunto de funciones.

El método de instrumentación inserta código en un archivo binario que captura información de tiempo de cada función en el archivo instrumentado y de cada llamada de función realizada por esas funciones. La instrumentación también identifica cuando una función llama al sistema operativo para operaciones como la escritura en un archivo. Los informes de instrumentación emplean cuatro valores para representar el tiempo total invertido en una función o una línea de código fuente:

- Inclusivo transcurrido: tiempo total dedicado a la ejecución de la función o la línea de código.

- Inclusivo de aplicación: tiempo dedicado a ejecutar la función o la línea de código fuente, excluyendo el tiempo invertido en llamadas al sistema operativo.

- Exclusivo transcurrido: tiempo dedicado a ejecutar el código del cuerpo de la función o la línea de código fuente. Se excluye el tiempo dedicado a ejecutar funciones llamadas por la función o la línea de código fuente.

- Exclusivo de aplicación: tiempo dedicado a ejecutar el código del cuerpo de la función o la línea de código fuente. Se excluye el tiempo dedicado a ejecutar llamadas al sistema operativo y el tiempo dedicado a ejecutar funciones llamadas por la función o la línea de código fuente.

Con el método de instrumentación también puede recopilar contadores de rendimiento de la CPU y el software.

[Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md)

[Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>simultaneidad

La generación de perfiles de simultaneidad recopila información sobre las aplicaciones multiproceso. La generación de perfiles de contención de recursos recopila información detallada de la pila de llamadas cada vez que subprocesos competidores se ven a obligados a esperar para obtener acceso a un recurso compartido. La visualización de simultaneidad también recopila información más general sobre la interacción de su aplicación multiproceso consigo misma, el hardware, el sistema operativo y otros procesos del equipo host.

- Los informes de contención de recursos muestran el número total de contenciones y el tiempo total invertido esperando a un recurso por los módulos, funciones, líneas del código fuente e instrucciones en los que se produjo la espera. Los gráficos de escala de tiempo también muestran las contenciones a medida que se produjeron.

- El visualizador de simultaneidad muestra información gráfica que se puede utilizar para buscar cuellos de botella de rendimiento, infrautilización de la CPU, contención de subprocesos, migración de subprocesos, retrasos de sincronización, áreas de E/S superpuestas y otra información. Cuando resulta posible, el gráfico vincula a los datos de la pila de llamadas y del código fuente. Solo se pueden recopilar datos de visualización de simultaneidad de la línea de comandos y las aplicaciones Windows.

[Descripción de los valores de datos de contención de recursos](../profiling/understanding-resource-contention-data-values.md)

[Recopilación de datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md)

[Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)

[Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Memoria de .NET

El método de generación de perfiles de asignación de memoria de .NET interrumpe el procesador del equipo en cada asignación de un objeto de .NET Framework en una aplicación cuyos perfiles se están generando. Cuando también se recopilan datos de duración de objetos, el generador de perfiles interrumpe el procesador después de cada recolección de elementos no utilizados de .NET Framework.

El generador de perfiles recopila información sobre el tipo, tamaño y número de objetos que se crearon en una asignación o se destruyeron en una recolección de elementos no utilizados.

- Cuando se produce un evento de asignación, el generador de perfiles recopila información adicional sobre la pila de llamadas a funciones. Los recuentos de asignación exclusivos se incrementan para la función que se está ejecutando en ese momento, mientras que los recuentos inclusivos se incrementan para todas las funciones de llamada de la pila de llamadas. Los informes de .NET presentan los totales de estos recuentos de los tipos, módulos, funciones, líneas de código fuente e instrucciones cuyos perfiles se están generando.

- Cuando se produce una recolección de elementos no utilizados, el generador de perfiles recopila datos sobre los objetos que se destruyeron y sobre los objetos de cada generación de recolección de elementos no utilizados. Al término de la generación de perfiles, el generador de perfiles registra datos sobre los objetos que no se destruyeron de forma explícita. El informe Duración del objeto muestra los totales de cada tipo asignado en la generación de perfiles.

La generación de perfiles de memoria de .NET se puede utilizar en el modo de muestreo o de instrumentación. El modo que seleccione no afecta a los informes Asignación y Duración del objeto, que son exclusivos de la generación de perfiles de memoria de .NET:

- Al ejecutar la generación de perfiles de memoria de .NET en modo de muestreo, el generador de perfiles de .NET utiliza los eventos de asignación de memoria como el intervalo y muestra el número de objetos que se asignaron y los bytes totales que se asignaron como los valores inclusivo y exclusivo de los informes.

- Al ejecutar la generación de perfiles de memoria de .NET en modo de instrumentación, se recopila información de tiempo detallada junto con los valores de asignación inclusivo y exclusivo.

[Descripción de los valores de datos de asignación de memoria y duración de objetos](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Recopilación de datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interacción de capas

La generación de perfiles de interacción de capas agrega información a un archivo de datos de generación de perfiles sobre llamadas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrónicas entre una página de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] u otra aplicación y una base de datos de [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Los datos incluyen el número y tiempo de llamadas y los tiempos máximo y mínimo. Los datos de interacción de capas se pueden agregar a los datos de generación de perfiles recopilados con los métodos de muestreo, instrumentación, memoria de .NET o simultaneidad.

![Datos de perfiles de interacción de capas](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

Datos de interacción de capas recopilados por las Herramientas de generación de perfiles

[Recopilación de datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)

[Vistas de interacción de capas](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Vea también

[Cómo: Recopilar datos de rendimiento de un sitio web](../profiling/how-to-collect-performance-data-for-a-web-site.md)
[Medición del rendimiento de aplicaciones mediante el análisis de uso de CPU](../profiling/beginners-guide-to-performance-profiling.md)
