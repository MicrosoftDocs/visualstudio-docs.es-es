---
title: Uso de los métodos de recopilación del rendimiento | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecbabae86b762c9143dba6be5aa0e4683a92b0dd
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250769"
---
# <a name="understand-performance-collection-methods"></a>Descripción de los métodos de recopilación de rendimiento

Las herramientas de generación de perfiles de Visual Studio proporcionan cinco métodos para recopilar datos de rendimiento. En este artículo se describen los distintos métodos y se sugieren algunos escenarios en los que puede resultar apropiado recopilar datos con un método determinado.

> [!NOTE]
> Las características de seguridad mejoradas de Windows 8 y Windows Server 2012 necesitaron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Vea [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Método|Descripción|
|------------|-----------------|
|[Muestreo](#sampling)|Recopila datos estadísticos sobre el trabajo realizado por una aplicación.|
|[Instrumentación](#instrumentation)|Recopila información de tiempo detallada sobre cada llamada a una función.|
|[Simultaneidad](#concurrency)|Recopila información detallada sobre las aplicaciones multiproceso.|
|[Memoria de .NET](#net-memory)|Recopila información detallada sobre la asignación de memoria de .NET y la recolección de elementos no utilizados.|
|[Interacción de capas](#tier-interaction)|Recopila información sobre las llamadas a funciones ADO.NET sincrónicas a una base de datos de SQL Server.<br /><br /> Todas las ediciones de Visual Studio pueden recopilar datos de perfil de interacción de capa. Sin embargo, solo puede ver esos datos en Visual Studio Enterprise.|

Con algunos de los métodos de generación de perfiles, también es posible recopilar datos adicionales, como contadores de rendimiento de software y hardware. Para obtener más información, consulte [Recopilación de datos de rendimiento adicionales](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Muestreo

El método de generación de perfiles de muestreo recopila datos estadísticos sobre el trabajo realizado por una aplicación durante una generación de perfiles. El método de muestreo consume pocos recursos y afecta poco a la ejecución de los métodos de la aplicación.

El muestreo es el método predeterminado de las herramientas de generación de perfiles de Visual Studio. Este método puede resultar útil para las siguientes tareas:

- Exploraciones iniciales del rendimiento de la aplicación.
- Investigación de problemas de rendimiento que implican la utilización del microprocesador (CPU).

El método de generación de perfiles de muestreo interrumpe la CPU del equipo a intervalos establecidos y recopila la pila de llamadas a funciones. Aumentan los recuentos de muestras exclusivos para la función que se ejecuta. Aumentan los recuentos inclusivos para todas las funciones de llamada de la pila de llamadas. Los informes de muestreo presentan los totales de estos recuentos de los módulos, las funciones, las líneas de código fuente y las instrucciones para los que se han generado perfiles.

De forma predeterminada, el generador de perfiles establece el intervalo de muestreo en los ciclos de la CPU. Puede cambiar el tipo de intervalo por otro contador de rendimiento de la CPU y establecer el número de eventos de contador del intervalo. También puede recopilar datos de generación de perfiles de interacción de capa (TIP). Estos datos proporcionan información sobre las consultas realizadas a una base de datos de SQL Server mediante ADO.NET.

[Recopilación de estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)

[Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentación

El método de generación de perfiles de instrumentación recopila información puntual detallada de las llamadas a funciones en una aplicación para la que se han generado perfiles. La generación de perfiles de instrumentación es útil para estas tareas:

- Investigación de cuellos de botella de entrada o salida, como E/S de disco.
- Examen exhaustivo de un módulo o un conjunto de funciones determinados.

El método de instrumentación inserta código en un archivo binario. El código captura información puntual de todas las funciones del archivo instrumentado y de cada llamada a función que realizan esas funciones. La instrumentación también identifica cuándo una función llama al sistema operativo para realizar operaciones como la escritura en un archivo.

Los informes de instrumentación emplean estos cuatro valores para representar el tiempo total empleado en una función o en una línea de código fuente:

- Inclusivo transcurrido: tiempo total dedicado a ejecutar la función o la línea de código fuente.

- Inclusivo de aplicación: tiempo dedicado a ejecutar la función o la línea de código fuente. Se excluyen las llamadas al sistema operativo.

- Exclusivo transcurrido: tiempo dedicado a ejecutar la función o la línea de código fuente. Se excluyen las llamadas a otras funciones.

- Exclusivo de aplicación: tiempo dedicado a ejecutar la función o la línea de código fuente. Se excluyen las llamadas al sistema operativo o a otras funciones.

Con el método de instrumentación también puede recopilar contadores de rendimiento de CPU y de software.

[Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md)

[Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>simultaneidad

La generación de perfiles de simultaneidad recopila información sobre las aplicaciones multiproceso. La generación de perfiles de contención de recursos recopila información detallada de la pila de llamadas cada vez que subprocesos competidores esperan el acceso a un recurso compartido. La visualización de simultaneidad también recopila información más general sobre cómo interactúa la aplicación multiproceso con:

- Ella misma.
- El hardware.
- Sistema operativo.
- Otros procesos del equipo host.

Los informes de contención de recursos muestran el número total de contenciones. También notifican el tiempo total que los módulos, las funciones, las líneas de código fuente y las instrucciones han esperado un recurso. Los gráficos de escala de tiempo muestran las contenciones a medida que se producen.

El visualizador de simultaneidad muestra información gráfica para ayudarlo a localizar:

- Los cuellos de botella de rendimiento.
- La infrautilización de la CPU.
- La contención de los subprocesos.
- La migración de los subprocesos.
- Los retrasos en la sincronización.
- Las áreas de E/S superpuestas.

  Cuando es posible, la salida del gráfico crea un vínculo a los datos desde la pila de llamadas y el código fuente. Solo se pueden recopilar datos de visualización de simultaneidad de las aplicaciones de línea de comandos y de las aplicaciones Windows.

[Descripción de los valores de datos de contención de recursos](../profiling/understanding-resource-contention-data-values.md)

[Recopilación de datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md)

[Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)

[Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Memoria de .NET

El método de generación de perfiles de asignación de memoria de .NET interrumpe la CPU en cada asignación de un objeto de .NET Framework en una aplicación para la que se han generado perfil. Cuando el generador de perfiles también recopila datos de duración de objetos, interrumpe la CPU después de cada recolección de elementos no utilizados de .NET Framework.

El generador de perfiles recopila información sobre el tipo, el tamaño y el número de objetos que se crearon en una asignación o se destruyeron en una recolección de elementos no utilizados.

- Cuando se produce un evento de asignación, el generador de perfiles recopila información adicional sobre la pila de llamadas a funciones. El generador de perfiles aumenta los recuentos de asignación exclusivos de la función actualmente en ejecución. También aumenta los recuentos inclusivos de todas las funciones de llamada de la pila de llamadas. Los informes de .NET presentan los totales de estos recuentos de los tipos, los módulos, las funciones, las líneas de código fuente y las instrucciones para los que se han generado perfiles.

- Cuando se produce una recolección de elementos no utilizados, el generador de perfiles recopila datos sobre los objetos destruidos y sobre los objetos de cada generación de recolección de elementos no utilizados. Al término de la generación de perfiles, el generador de perfiles registra datos sobre los objetos que no se destruyeron de forma explícita. En el informe de duración de objetos se muestran los totales de cada tipo asignado en la generación de perfiles.

Puede usar la generación de perfiles de memoria de .NET en modo de muestreo o de instrumentación. El modo que seleccione no afecta a los informes de asignación y duración de objetos, que son exclusivos de la generación de perfiles de memoria de .NET.

- Al ejecutar la generación de perfiles de memoria de .NET en modo de muestreo, el generador de perfiles utiliza eventos de asignación de memoria como intervalo. También muestra el número total de objetos y bytes asignados como valores inclusivos y exclusivos de los informes.

- Al ejecutar la generación de perfiles de memoria de .NET en modo de instrumentación, el generador de perfiles recopila información puntual detallada junto con los valores de asignación inclusivos y exclusivos.

[Descripción de los valores de datos de asignación de memoria y duración de objetos](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Recopilación de datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interacción de capas

La generación de perfiles de interacción de capa agrega información a un archivo de datos de generación de perfiles sobre las llamadas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrónicas entre una página de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] u otra aplicación y una base de datos de [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Los datos incluyen el número y el tiempo de las llamadas y los tiempos máximo y mínimo. Puede agregar datos de interacción de capa a datos de generación de perfiles que se recopilen con los métodos de simultaneidad, muestreo, instrumentación o memoria de .NET.

![Flujo de datos de generación de perfiles de interacción de capa](../profiling/media/tierinteraction_profilingtools.png "Flujo de datos de generación de perfiles de interacción de capa")

Para información sobre los datos de interacción de capa recopilados con las herramientas de generación de perfiles, consulte los siguientes artículos.

[Recopilación de datos de interacción de capa](../profiling/collecting-tier-interaction-data.md)

[Vistas de interacción de capa](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Vea también

[Cómo: Recopilar datos de rendimiento de un sitio web](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)
