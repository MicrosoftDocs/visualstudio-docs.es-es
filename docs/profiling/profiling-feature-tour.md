---
title: Introducción a las herramientas de generación de perfiles
description: Eche un vistazo breve a las distintas herramientas de diagnóstico disponibles en Visual Studio.
ms.custom: ''
ms.date: 09/08/2020
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfd7055303fed2c18501d5eea3b49b34c68ec248
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929113"
---
# <a name="first-look-at-profiling-tools"></a>Un primer vistazo a las herramientas de generación de perfiles

Visual Studio proporciona una variedad de herramientas de generación de perfiles que le ayudarán a diagnosticar diferentes tipos de problemas de rendimiento según el tipo de aplicación. En este artículo, echamos un vistazo rápido a las herramientas de generación de perfiles más habituales.

Para ver la compatibilidad de la herramienta de generación de perfiles con los distintos tipos de aplicaciones, consulte [¿Qué herramienta debo usar?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Medición del rendimiento durante la depuración

Las herramientas de generación de perfiles a las que puede obtener acceso durante una sesión de depuración están disponibles en la ventana Herramientas de diagnóstico. La ventana Herramientas de diagnóstico aparece automáticamente a menos que la desactive. Para mostrar la ventana, haga clic en **Depurar / Windows / Mostrar herramientas de diagnóstico**. Con la ventana abierta, puede seleccionar las herramientas para las que se van a recopilar datos.

![Ventana Herramientas de diagnóstico](../profiling/media/prof-tour-diagnostic-tools.png "Herramientas de diagnóstico")

Durante la depuración, puede usar la ventana **Herramientas de diagnóstico** para analizar la CPU y el uso de memoria, y puede ver los eventos que muestran información relacionada con el rendimiento.

![Vista de resumen de Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Resumen de Herramientas de diagnóstico")

La ventana **Herramientas de diagnóstico** es una manera habitual de generar perfiles de aplicaciones, pero en el caso de las compilaciones de versión, también puede hacer un análisis posterior de la aplicación. Para más información sobre los diferentes enfoques, consulte [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Para ver la compatibilidad de la herramienta de generación de perfiles con los distintos tipos de aplicaciones, consulte [¿Qué herramienta debo usar?](#which-tool-should-i-use)

Las herramientas disponibles en la ventana Herramientas de diagnóstico o durante una sesión de depuración incluyen:
- [Uso de CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Uso de memoria](../profiling/memory-usage.md)
- [Sugerencias de rendimiento](../profiling/perftips.md)

> [!NOTE]
> Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**). Puede usar las herramientas de análisis [final](#post_mortem) con Windows 7 y versiones posteriores. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Medición del rendimiento en compilaciones de versión

Las herramientas del Generador de perfiles de rendimiento están diseñadas para proporcionar análisis de las compilaciones de **versión**. En el Generador de perfiles de rendimiento, puede recopilar información de diagnóstico mientras se ejecuta la aplicación y, después, examinar la información recopilada cuando la aplicación se haya detenido (un análisis final).

Para abrir el Generador de perfiles de rendimiento, seleccione **Depurar** > **Generador de perfiles de rendimiento** (o **Alt + F2**).

![Generador de perfiles de rendimiento](../profiling/media/prof-tour-performance-profiler.png "Generador de perfiles de rendimiento")

Para más información sobre el uso de la herramienta Uso de CPU o Uso de memoria en el Generador de perfiles de rendimiento frente a las herramientas integradas en el depurador, consulte [Ejecución de herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Las herramientas disponibles en el Generador de perfiles de rendimiento incluyen:

- [Uso de CPU](../profiling/cpu-usage.md)
- [Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md)
- [Uso de memoria](../profiling/memory-usage-without-debugging2.md)
- [Herramienta asincrónica de .NET](../profiling/analyze-async.md)
- [Herramienta de base de datos](../profiling/analyze-database.md)
- [Uso de GPU](../profiling/gpu-usage.md)

Para ver la compatibilidad de la herramienta de generación de perfiles con los distintos tipos de aplicaciones, consulte [¿Qué herramienta debo usar?](#which-tool-should-i-use)

En algunos escenarios, la ventana le permite seleccionar [varias herramientas de generación de perfiles](../profiling/use-multiple-profiler-tools-simultaneously.md). Las herramientas como Uso de CPU proporcionan datos complementarios que le pueden ayudar en el análisis. También puede usar el [generador de perfiles de la línea de comandos](../profiling/profile-apps-from-command-line.md) para habilitar escenarios con varias herramientas de generación de perfiles.

## <a name="examine-performance-using-perftips"></a>Examen del rendimiento mediante PerfTips

A menudo, la manera más sencilla de ver la información de rendimiento es mediante el uso de [PerfTips](../profiling/perftips.md). Con PerfTips, se puede ver información de rendimiento mientras se interactúa con el código. Puede comprobar información como la duración del evento, medida desde el momento en que el depurador se ha detenido por última vez o desde que se ha iniciado la aplicación. Por ejemplo, si se revisa paso a paso el código (F10, F11), PerfTips muestra la duración en tiempo de ejecución de la aplicación, desde la operación del paso anterior hasta el paso actual.

![Sugerencias de rendimiento en Paseo por la generación de perfiles](../profiling/media/prof-tour-perf-tips.png "Sugerencias de rendimiento en Paseo por la generación de perfiles")

Puede usar PerfTips para examinar cuánto tiempo tarda un bloque de código en ejecutarse o en completarse una sola función.

PerfTips muestra los mismos eventos que también se muestran en la vista **Eventos** de las Herramientas de diagnóstico. En la vista **Eventos** se pueden ver eventos distintos que se producen durante la depuración, como la configuración de un punto de interrupción o una operación de procesamiento de código paso a paso.

![Vista de eventos en Herramientas de diagnóstico](../profiling/media/prof-tour-events.png "Vista de eventos en Herramientas de diagnóstico")

 > [!NOTE]
 > Si tiene Visual Studio Enterprise, también puede ver [Eventos de IntelliTrace](../debugger/intellitrace.md) en esta pestaña.

## <a name="analyze-cpu-usage"></a>Analizar el uso de CPU

La herramienta Uso de CPU es un buen lugar para empezar a analizar el rendimiento de la aplicación. Le proporcionará más información sobre los recursos de CPU que consume la aplicación. Puede usar la [herramienta Uso de CPU integrada en el depurador](../profiling/beginners-guide-to-performance-profiling.md) o la [herramienta Uso de CPU de análisis final](../profiling/cpu-usage.md).

Al usar la herramienta Uso de CPU integrada en el depurador, abra la ventana Herramientas de diagnóstico (si está cerrada, elija **Depurar / Ventanas / Mostrar Herramientas de diagnóstico**). Durante la depuración, abra la vista **Resumen** y seleccione **Registrar perfil CPU**.

![Habilitar el uso de CPU en Herramientas de diagnóstico](../profiling/media/prof-tour-enable-cpu-profiling.png "Habilitar el uso de CPU en Herramientas de diagnóstico")

Una forma de usar la herramienta es establecer dos puntos de interrupción en el código, uno al principio y otro al final de la función o la región de código que quiere analizar. Examine los datos de generación de perfiles cuando se haya detenido en el segundo punto de interrupción.

La vista **Uso de CPU** muestra una lista de funciones ordenadas por la ejecución más larga, con la función más larga que se está ejecutando en la parte superior. Esto le ayudará a detectar las funciones en las que se producen cuellos de botella de rendimiento.

![Vista Uso de CPU de Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-usage.png "Uso de CPU de Herramientas de diagnóstico")

Si hace doble clic en una función que le interese, verá una vista de "mariposa" de tres paneles más detallada, con la función seleccionada en el centro de la ventana, la función de llamada a la izquierda y las funciones llamadas a la derecha. En la sección **Cuerpo de la función** se muestra la cantidad total de tiempo (y el porcentaje de tiempo) empleado en el cuerpo de la función, excluido el tiempo invertido en las funciones de llamada y las funciones llamadas. Estos datos pueden ayudarle a evaluar si la función en sí es un cuello de botella de rendimiento.

![Vista de "mariposa" Llamador y destinatario en Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Vista Llamador y destinatario de Herramientas de diagnóstico")

## <a name="analyze-memory-usage"></a>Analizar el uso de memoria

La ventana **Herramientas de diagnóstico** permite evaluar el uso de memoria en la aplicación mediante la herramienta **Uso de memoria**. Por ejemplo, puede buscar el número y el tamaño de los objetos del montón. Puede usar la [herramienta Uso de memoria integrada en el depurador](../profiling/memory-usage.md) o la [herramienta Uso de memoria de análisis final](../profiling/memory-usage-without-debugging2.md) del Generador de perfiles de rendimiento.

Los desarrolladores de .NET pueden elegir entre la [herramienta de asignación de objetos .NET](../profiling/dotnet-alloc-tool.md) o la herramienta [Uso de memoria](../profiling/memory-usage.md).

- La **herramienta de asignación de objetos .NET** ayuda a identificar patrones de asignación y anomalías en el código de .NET, además de problemas habituales en la recolección de elementos no utilizados. Esta herramienta solo se ejecuta a modo de análisis post mortem. Puede ejecutar esta herramienta en máquinas locales o remotas.
- La herramienta **Uso de memoria** es útil para identificar fugas de memoria, que no suelen ser habituales en aplicaciones .NET. Si necesita usar características del depurador mientras comprueba la memoria, como ejecutar paso a paso el código, se recomienda la herramienta [Uso de memoria integrada en el depurador](../profiling/beginners-guide-to-performance-profiling.md).

Para analizar el uso de memoria con la herramienta **Uso de memoria**, se debe tomar al menos una instantánea de memoria. A menudo, la mejor manera de analizar la memoria consiste en tomar dos instantáneas: la primera justo antes de que se produzca un problema que sospecha que existe en la memoria y la segunda después de que se produzca el problema en cuestión. Después, puede ver las diferencias que existen entre las dos instantáneas y constatar qué es lo que ha cambiado exactamente. En la ilustración siguiente se muestra cómo tomar una instantánea con la herramienta integrada en el depurador.

![Toma de una instantánea en Herramientas de diagnóstico](../profiling/media/prof-tour-take-snapshots.gif "Tomar instantáneas en Herramientas de diagnóstico")

Al seleccionar uno de los vínculos de flecha, aparece una vista diferencial del montón (una flecha hacia arriba de color rojo ![Aumento en el uso de memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento del uso de memoria") muestra un número de objetos creciente (izquierda) o un tamaño de montón creciente (derecha)). Si hace clic en el vínculo de la derecha, obtendrá una vista diferencial del montón ordenada por los objetos que más han aumentado en el tamaño del montón. Esto puede ayudarle a identificar problemas de memoria. Por ejemplo, en la ilustración siguiente, los bytes usados por los objetos `ClassHandlersStore` han aumentado 3,492 bytes en la segunda instantánea.

![Vista de diferencias del montón en Herramientas de diagnóstico](../profiling/media/prof-tour-mem-usage-diff-heap.png "Vista de diferencias del montón en Herramientas de diagnóstico")

En cambio, si hace clic en el vínculo de la izquierda en la vista **Uso de memoria**, la vista del montón se organiza por número de objetos y se muestran los objetos de un tipo determinado que más han aumentado en número en la parte superior (ordenados por la columna **Dif. de recuento**).

## <a name="analyze-resource-consumption-xaml"></a>Análisis del consumo de recursos (XAML)

En las aplicaciones XAML (como las aplicaciones de WPF de escritorio de Windows y las aplicaciones para UWP), puede analizar el consumo de recursos mediante la herramienta Escala de tiempo de la aplicación. Por ejemplo, puede analizar el tiempo consumido por la aplicación en la preparación de marcos de la interfaz de usuario (diseño y presentación), la atención de solicitudes de red y de disco y escenarios como el inicio de la aplicación, carga de la página y cambio de tamaño de las ventanas. Para usar la herramienta, seleccione **Escala de tiempo de la aplicación** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario en el que sospecha que se produce un problema de consumo de recursos y, después, seleccione **Detener recolección** para generar el informe.

Los valores de framerate bajos en el gráfico **Rendimiento visual** podrían corresponderse con los problemas visuales que ve cuando se ejecuta la aplicación. De forma similar, los números elevados en el gráfico **Uso del subproceso de UI** podrían corresponderse con problemas en la capacidad de respuesta de la interfaz de usuario. En el informe, puede seleccionar un período de tiempo en el que sospecha que se produce un problema de rendimiento y, después, examinar las actividades detalladas del subproceso de interfaz de usuario en la vista Detalles de la escala de tiempo (panel inferior).

![Herramienta de generación de perfiles de Escala de tiempo de la aplicación](../profiling/media/prof-tour-application-timeline.gif "Escala de tiempo de la aplicación en Paseo por la generación de perfiles")

En la vista Detalles de la escala de tiempo, puede encontrar información como el tipo de actividad (o el elemento de la interfaz de usuario implicado) junto con la duración de la actividad. Por ejemplo, en la ilustración, un evento de **Diseño** para un control de cuadrícula tarda 57,53 ms.

Para obtener más información, vea [Application Timeline](../profiling/application-timeline.md) (Escala de tiempo de la aplicación).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Examen de eventos de aplicaciones

El [visor de eventos](../profiling/events-viewer.md) genérico permite ver la actividad de la aplicación a través de una lista de eventos, como configuraciones del sistema, inicio de subprocesos y carga de módulos, para ayudar a realizar un mejor diagnóstico del rendimiento de la aplicación en el generador de perfiles de Visual Studio. Esta herramienta está disponible en el generador de perfiles de rendimiento. Para abrir el Generador de perfiles de rendimiento, seleccione **Depurar** > **Generador de perfiles de rendimiento** (o **Alt + F2**).

La herramienta muestra cada evento en una vista de lista. Las columnas proporcionan información sobre cada evento, como el nombre del evento, la marca de tiempo y el identificador de proceso.

![Seguimiento del visor de eventos](../profiling/media/eventviewertrace.png "Seguimiento del visor de eventos")

## <a name="analyze-asynchronous-code-net"></a>Análisis de código asincrónico (.NET)

La [herramienta .NET Async](../profiling/analyze-async.md) permite analizar el rendimiento del código asincrónico en la aplicación. Esta herramienta está disponible en el generador de perfiles de rendimiento. Para abrir el Generador de perfiles de rendimiento, seleccione **Depurar** > **Generador de perfiles de rendimiento** (o **Alt + F2**).

La herramienta muestra cada operación asincrónica en una vista de lista. Puede ver información como la hora de inicio, la hora de finalización y el tiempo total de una operación asincrónica.

![Herramienta .NET Async detenida](../profiling/media/async-tool-opened.png "Herramienta .NET Async detenida")

## <a name="analyze-database-performance-net-core"></a>Análisis del rendimiento de base de datos (.NET Core)

En el caso de las aplicaciones .NET Core que usan ADO.NET o Entity Framework Core, la [herramienta de base de datos](../profiling/analyze-database.md) permite registrar las consultas de base de datos realizadas por la aplicación durante una sesión de diagnóstico. A continuación, puede analizar la información sobre consultas individuales para buscar dónde se puede mejorar el rendimiento de la aplicación. Esta herramienta está disponible en el generador de perfiles de rendimiento. Para abrir el Generador de perfiles de rendimiento, seleccione **Depurar** > **Generador de perfiles de rendimiento** (o **Alt + F2**).

La herramienta muestra cada consulta en una vista de lista. Puede ver información como la hora de inicio y la duración de la consulta.

![Asignación](./media/db-gotosource.png "Asignación")

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examinar eventos de accesibilidad y rendimiento de la interfaz de usuario (UWP)

En las aplicaciones de UWP, puede habilitar **Análisis de UI** en la ventana **Herramientas de diagnóstico**. La herramienta busca problemas comunes de rendimiento o de accesibilidad y los muestra en la vista **Eventos** durante la depuración. Las descripciones de los eventos proporcionan información que puede ayudar a resolver problemas.

![Vista de eventos de análisis de la interfaz de usuario en las herramientas de diagnóstico](../profiling/media/prof-tour-ui-analysis.png "Vista de eventos de análisis de la interfaz de usuario en Herramientas de diagnóstico")

## <a name="analyze-gpu-usage-direct3d"></a>Análisis del uso de la GPU (Direct3D)

En las aplicaciones Direct3D (los componentes Direct3D deben estar en C++), puede examinar la actividad de la GPU y analizar problemas de rendimiento. Para obtener más información, vea [GPU Usage](./gpu-usage.md) (Uso de GPU). Para usar la herramienta, seleccione **Uso de GPU** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario del que le interesa generar un perfil y, después, seleccione **Detener recolección** para generar un informe.

Si elige un período de tiempo en los gráficos y selecciona **Ver detalles**, aparece una vista detallada en el panel inferior. En la vista detallada, puede examinar cuántas actividades se producen en cada CPU y GPU. Seleccione los eventos en el panel inferior para que aparezcan elementos emergentes en la escala de tiempo. Por ejemplo, seleccione el evento **Presente** para ver elementos emergentes de llamada **Presente**. (Las líneas de sincronización vertical de color gris claro se pueden usar como referencia para entender si alguna llamada **Presente** ha perdido la sincronización vertical. Debe haber una llamada **Presente** entre cada dos sincronizaciones verticales para que la aplicación alcance constantemente los 60 fps).

![Herramienta de generación de perfiles de uso de GPU](../profiling/media/prof-tour-gpu-usage.png "Diagrama de uso de GPU")

También puede usar los gráficos para determinar si hay cuellos de botella de rendimiento relacionados con la CPU o con la GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Análisis de rendimiento (JavaScript UWP)

En el caso de las aplicaciones UWP, puede usar la herramienta Memoria de JavaScript y la herramienta Capacidad de respuesta de la IU HTML.

La herramienta Memoria de JavaScript es similar a la herramienta Uso de memoria disponible para otros tipos de aplicaciones. Puede usar esta herramienta para entender el uso de memoria y buscar fugas de memoria en la aplicación. Para obtener más información sobre la herramienta, vea [JavaScript Memory](../profiling/javascript-memory.md) (Memoria de JavaScript).

![Herramienta de generación de perfiles de Memoria de JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Para diagnosticar la capacidad de respuesta de la interfaz de usuario, el tiempo de carga lento y las actualizaciones visuales lentas en aplicaciones UWP, use la herramienta Capacidad de respuesta de la IU HTML. El uso es similar al de la herramienta Escala de tiempo de la aplicación para otros tipos de aplicaciones. Para obtener más información, vea [HTML UI responsiveness](../profiling/html-ui-responsiveness.md) (Capacidad de respuesta de IU HTML).

![Herramienta de generación de perfiles de Respuesta de IU de HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Análisis del uso de la red (UWP)

En las aplicaciones para UWP, puede analizar las operaciones de red realizadas mediante la API `Windows.Web.Http`. Esta herramienta puede ayudarle a resolver problemas como los problemas de acceso y autenticación, uso incorrecto de la caché y rendimiento deficiente de visualización y descarga. Para usar la herramienta, seleccione **Red** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Herramienta de generación de perfiles de uso de red](../profiling/media/prof-tour-network-usage.png "Diagrama de Uso de red")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta Uso de red](../profiling/media/prof-tour-network-usage-details.png "Diagrama de Detalles de uso de la red")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Análisis de rendimiento (herramientas heredadas)

::: moniker range="vs-2017"
Si necesita características que no están actualmente presentes en las herramientas Uso de CPU o Uso de memoria, como la instrumentación, y ejecuta aplicaciones ASP.NET o de escritorio, puede usar el Explorador de rendimiento para la generación de perfiles. (No se admite en aplicaciones UWP). Para más información, vea [Explorador de rendimiento](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
En Visual Studio 2019, el Explorador de rendimiento heredado y las herramientas de generación de perfiles relacionadas, como el Asistente de rendimiento, se han incorporado al Generador de perfiles de rendimiento, que se puede abrir mediante **Depurar** > **Generador de perfiles de rendimiento**. En el Generador de perfiles de rendimiento, las herramientas de diagnóstico disponibles dependen del destino elegido y del proyecto de inicio abierto actual. La herramienta Uso de CPU proporciona la capacidad de muestreo anteriormente admitida en el Asistente de rendimiento. La herramienta Instrumentación proporciona la capacidad de generación de perfiles instrumentada (para recuentos y duraciones de llamadas precisos) que se encontraba en el Asistente de rendimiento. En el Generador de perfiles de rendimiento, además, aparecen otras herramientas de memoria.
::: moniker-end

![Herramienta Explorador de rendimiento](../profiling/media/prof-tour-performance-explorer.png "Explorador de rendimiento")

## <a name="which-tool-should-i-use"></a>¿Qué herramienta debo usar?

En esta tabla se muestra una lista de las distintas herramientas que ofrece Visual Studio y los tipos de proyecto con los que las puede usar:

::: moniker range=">=vs-2019"
|Herramienta de rendimiento|Escritorio de Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Sugerencias de rendimiento](../profiling/perftips.md)|sí|sí|sí|
|[Uso de CPU](../profiling/beginners-guide-to-performance-profiling.md)|sí|sí|sí|
|[Uso de memoria](../profiling/memory-usage.md)|sí|sí|sí|
|[Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md)|sí (solo .NET)|sí|sí|
|[Uso de GPU](./gpu-usage.md)|sí|sí|no|
|[Escala de tiempo de la aplicación](../profiling/application-timeline.md)|sí (XAML)|sí|No|
|[Visor de eventos](../profiling/events-viewer.md)|sí|sí|sí|
|[.NET Async](../profiling/analyze-async.md)|sí (solo .NET)|sí|sí|
|[Base de datos](../profiling/analyze-database.md)|sí (solo .NET Core)|No|sí (solo ASP.NET Core)|
|[Explorador de rendimiento](#analyze-performance-legacy-tools)|No|no|No|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Herramienta de rendimiento|Escritorio de Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Uso de CPU](../profiling/beginners-guide-to-performance-profiling.md)|sí|sí|sí|
|[Uso de memoria](../profiling/memory-usage.md)|sí|sí|sí|
|[Uso de GPU](./gpu-usage.md)|sí|sí|no|
|[Escala de tiempo de la aplicación](../profiling/application-timeline.md)|sí (XAML)|sí|No|
|[Sugerencias de rendimiento](../profiling/perftips.md)|sí|sí para XAML, no para HTML|sí|
|[Explorador de rendimiento](../profiling/performance-explorer.md)|sí|no|sí|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
|[Uso de red](../profiling/network-usage.md)|No|sí|No|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|No|sí para HTML, no para XAML|No|
|[Memoria de JavaScript](../profiling/javascript-memory.md)|No|sí para HTML, no para XAML|No|
::: moniker-end


## <a name="see-also"></a>Vea también
- [Depurar en Visual Studio](../debugger/debugger-feature-tour.md)