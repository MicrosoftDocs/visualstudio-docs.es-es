---
title: Optimización de la configuración del generador de perfiles | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9ff76364026230d08d03c91d14bddba3c325e7be
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291056"
---
# <a name="optimizing-profiler-settings"></a>Optimización de la configuración del generador de perfiles

Las ventanas Generador de perfiles de rendimiento y Herramientas de diagnóstico de Visual Studio tienen muchas configuraciones distintas que afectan el rendimiento general de las herramientas. Cambiar algunos valores de configuración puede hacer que el análisis se ejecute rápidamente o provocar tiempos de espera adicionales mientras se procesan los resultados en las herramientas. A continuación se muestra un resumen de ciertas configuraciones y su impacto en el rendimiento.

## <a name="symbol-settings"></a>Valores de los símbolos

La configuración de símbolos que se encuentra en las opciones del depurador (**Depurar > Opciones > Símbolos**) tiene un impacto significativo en el tiempo que se tarda en generar resultados en las herramientas. La habilitación de servidores de símbolos o el uso de **_NT_SYMBOL_PATH** hace que el generador de perfiles solicite símbolos para cada módulo cargado en un informe. Actualmente, el generador de perfiles siempre carga automáticamente todos los símbolos independientemente de la preferencia de carga automática de símbolos.

![Página de carga de símbolos](../profiling/media/symbolloading.png "Carga de símbolos")

El progreso de la carga de símbolos se puede ver en la ventana **Salida** bajo el encabezado **Herramientas de diagnóstico**.

![Progreso de la carga de símbolos](../profiling/media/symbolloadingprogress.png "Progreso de la carga de símbolos")

Una vez que se descargan, los símbolos se almacenan en caché, lo que acelerará el análisis futuro pero seguirá siendo necesario cargar y analizar los archivos. Si la carga de símbolos ralentiza el análisis, intente desactivar los servidores de símbolos y borrar la caché de símbolos. En su lugar, básese en los símbolos compilados localmente para el proyecto.

## <a name="show-external-code"></a>Mostrar código externo

Muchas de las herramientas dentro de las ventanas **Generador de perfiles de rendimiento** y **Herramientas de diagnóstico** tienen un concepto de código de usuario frente a código externo. El código de usuario es cualquier código compilado por la solución abierta o el área de trabajo abierta. El código externo es todo lo demás. Si mantiene la opción **Mostrar código externo** deshabilitada o la opción **Mostrar solo mi código** habilitada, permite que las herramientas agreguen código externo a un solo fotograma de primer nivel, lo que reduce en gran medida la cantidad de procesamiento necesario para mostrar los resultados. Esto permite a los usuarios ver lo que se llamó en el código externo que creó la ralentización mientras se mantiene el procesamiento de los datos en un mínimo. Cuando sea posible, deje la opción **Mostrar código externo** deshabilitada y asegúrese de que tiene abierta la solución o el área de trabajo para la sesión de diagnóstico que está analizando.

## <a name="trace-duration"></a>Duración del seguimiento

La generación de perfiles de duraciones menores genera menos datos, lo que es más rápido de analizar. Por lo general, se recomienda intentar limitar los seguimientos a menos de cinco minutos de datos de rendimiento. Algunas herramientas, como la herramienta [Uso de CPU](../profiling/cpu-usage.md), permiten pausar la recopilación de datos mientras se ejecuta la herramienta, de modo que puede limitar la cantidad de datos que se recopilan en el escenario que le interesa analizar.

## <a name="sampling-frequency"></a>Frecuencia de muestreo

Ciertas herramientas, como las herramientas [Uso de CPU](../profiling/cpu-usage.md) y [Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md), le permiten ajustar una frecuencia de muestreo. Aumentar esta frecuencia de muestreo permite realizar mediciones con mayor precisión, pero aumenta la cantidad de datos que se generan. Por lo general, es mejor dejar esta configuración a la velocidad predeterminada, a menos que se investigue un problema específico.

![Página de propiedades del concentrador de diagnóstico](../profiling/media/diaghubpropertiespage.png "Página de propiedades del concentrador de diagnóstico")

## <a name="see-also"></a>Vea también

- [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Uso de varias herramientas de generación de perfiles de forma simultánea](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Descripción de los métodos de colección de rendimiento](../profiling/understanding-performance-collection-methods-perf-profiler.md)
