---
title: "Guía de características de generación de perfiles | Microsoft Docs"
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4899f59362f623f6ecf92927e8a15ed4762fa367
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2017
---
# <a name="profiling-feature-tour"></a>Guía de características de generación de perfiles

Visual Studio proporciona una variedad de herramientas de generación de perfiles que le ayudarán a diagnosticar diferentes tipos de problemas de rendimiento según el tipo de aplicación.

Las herramientas de generación de perfiles a las que puede obtener acceso durante una sesión de depuración están disponibles en la ventana Herramientas de diagnóstico. La ventana Herramientas de diagnóstico aparece automáticamente a menos que la desactive. Para mostrar la ventana, haga clic en **Depurar / Windows / Mostrar herramientas de diagnóstico**. Con la ventana abierta, puede seleccionar las herramientas para las que se van a recopilar datos.

![Ventana Herramientas de diagnóstico](../profiling/media/prof-tour-diagnostic-tools.png "Herramientas de diagnóstico")

Durante la depuración, puede usar la ventana **Herramientas de diagnóstico** para analizar la CPU y el uso de memoria, y puede ver los eventos que muestran información relacionada con el rendimiento.

![Vista de Resumen de Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Resumen de Herramientas de diagnóstico")

La ventana **Herramientas de diagnóstico** suele ser la mejor manera de generar perfiles de aplicaciones, pero también puede hacer un análisis posterior de la aplicación. Para obtener más información sobre los diferentes enfoques, vea [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Ejecutar herramientas de generación de perfiles con o sin el depurador).

## <a name="analyze-cpu-usage"></a>Analizar el uso de CPU

La herramienta Uso de CPU es un buen lugar para empezar a analizar el rendimiento de la aplicación. Le proporcionará más información sobre los recursos de CPU que consume la aplicación. Para obtener un tutorial más detallado de la herramienta Uso de CPU, vea [Beginner's Guide to Performance Profiling](../profiling/beginners-guide-to-performance-profiling.md) (Guía básica para la generación de perfiles de rendimiento).

En la vista **Resumen** de Herramientas de diagnóstico, seleccione **Habilitar generación de perfiles de CPU** (debe estar en una sesión de depuración).

![Habilitar el uso de CPU en las Herramientas de diagnóstico](../profiling/media/prof-tour-enable-cpu-profiling.png "Habilitar uso de CPU en Herramientas de diagnóstico")

Para usar la herramienta de la forma más eficaz posible, establezca dos puntos de interrupción en el código, uno al principio y otro al final de la función o la región de código que quiere analizar. Examine los datos de generación de perfiles cuando se haya detenido en el segundo punto de interrupción.

La vista **Uso de CPU** muestra una lista de funciones ordenadas por la ejecución más larga, con la función más larga que se está ejecutando en la parte superior. Esto le ayudará a detectar las funciones en las que se producen cuellos de botella de rendimiento.

![Vista de Uso de CPU de Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-usage.png "Uso de CPU de Herramientas de diagnóstico")

Si hace doble clic en una función que le interese, verá una vista de "mariposa" de tres paneles más detallada, con la función seleccionada en el centro de la ventana, la función de llamada a la izquierda y las funciones llamadas a la derecha. En la sección **Cuerpo de la función** se muestra la cantidad total de tiempo (y el porcentaje de tiempo) empleado en el cuerpo de la función, excluido el tiempo invertido en las funciones de llamada y las funciones llamadas. Estos datos pueden ayudarle a evaluar si la función en sí es un cuello de botella de rendimiento.

![Vista de "mariposa" de llamador y destinatario de Herramientas de diagnóstico](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Vista de llamador y destinatario de Herramientas de diagnóstico")

## <a name="analyze-memory-usage"></a>Analizar el uso de memoria

La ventana Herramientas de diagnóstico permite evaluar el uso de memoria en la aplicación. Por ejemplo, puede buscar el número y el tamaño de los objetos del montón. Para instrucciones más detalladas sobre el análisis de la memoria, vea [Analyze Memory Usage](../profiling/memory-usage.md) (Análisis del uso de memoria).

Para analizar el uso de memoria, debe tomar al menos una instantánea de memoria durante la depuración. A menudo, la mejor manera de analizar la memoria consiste en tomar dos instantáneas: la primera justo antes de que se produzca un problema que sospecha que existe en la memoria y la segunda después de que se produzca el problema en cuestión. Después, puede ver las diferencias que existen entre las dos instantáneas y constatar qué es lo que ha cambiado exactamente.

![Tomar una instantánea de las Herramientas de diagnóstico](../profiling/media/prof-tour-take-snapshots.gif "Tomar instantáneas de Herramientas de diagnóstico")

Al seleccionar uno de los vínculos de flecha, aparece una vista diferencial del montón. Una flecha roja hacia arriba ![Aumento en el uso de memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento en el uso de memoria") muestra un número de objetos creciente (izquierda) o un tamaño de montón creciente (derecha). Si hace clic en el vínculo de la derecha, obtendrá una vista diferencial del montón ordenada por los objetos que más han aumentado en el tamaño del montón. Esto puede ayudarle a identificar problemas de memoria. Por ejemplo, en la ilustración siguiente, los bytes usados por los objetos `ClassHandlersStore` han aumentado 3,492 bytes en la segunda instantánea.

![Vista de diferencia de montón en Herramientas de diagnóstico](../profiling/media/prof-tour-mem-usage-diff-heap.png "Vista de diferencia de montón en Herramientas de diagnóstico")

En cambio, si hace clic en el vínculo de la izquierda en la vista **Uso de memoria**, la vista del montón se organiza por número de objetos y se muestran los objetos de un tipo determinado que más han aumentado en número en la parte superior (ordenados por la columna **Dif. de recuento**).

## <a name="examine-performance-events"></a>Examinar eventos de rendimiento

La vista **Eventos** de Herramientas de diagnóstico muestra diversos eventos que se producen durante la depuración, como la configuración de un punto de interrupción o una operación de ejecución paso a paso de código. Puede comprobar información como la duración del evento, medida desde el momento en que el depurador se ha detenido por última vez o desde que se ha iniciado la aplicación. Por ejemplo, si recorre paso a paso el código (F10, F11), en la vista **Eventos** se muestra la duración en tiempo de ejecución de la aplicación desde la operación del paso anterior hasta el paso actual.

![Ver eventos de Herramientas de diagnóstico](../profiling/media/prof-tour-events.png "Ver eventos de Herramientas de diagnóstico")

 > [!NOTE]
 > Si tiene Visual Studio Enterprise, también puede ver [Eventos de IntelliTrace](../debugger/intellitrace.md) en esta pestaña.

En el editor de código también se muestran los mismos eventos, que puede ver como sugerencias de rendimiento.

![Sugerencias de rendimiento en la guía de generación de perfiles](../profiling/media/prof-tour-perf-tips.png "Sugerencias de rendimiento en la guía de generación de perfiles")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examinar el rendimiento de la interfaz de usuario y los eventos de accesibilidad (UWP)

En las aplicaciones UWP, puede habilitar **Análisis de UI** en la ventana Herramientas de diagnóstico. La herramienta busca problemas comunes de rendimiento o de accesibilidad y los muestra en la vista **Eventos** durante la depuración. Las descripciones de los eventos proporcionan información que puede ayudar a resolver problemas.

![Ver eventos del Análisis de UI en las Herramientas de diagnóstico](../profiling/media/prof-tour-ui-analysis.png "Ver eventos del Análisis de UI de Herramientas de diagnóstico")

## <a name="profile-release-builds-without-the-debugger"></a>Generar perfiles de compilaciones de versión sin el depurador

Las herramientas de generación de perfiles como Uso de CPU y Uso de memoria pueden usarse con el depurador (vea las secciones anteriores) o bien se pueden ejecutar mediante el Generador de perfiles de rendimiento, que está diseñado para proporcionar el análisis de compilaciones de **Versión**. En el Generador de perfiles de rendimiento, puede recopilar información de diagnóstico mientras se ejecuta la aplicación y, después, examinar la información recopilada cuando la aplicación se haya detenido. Para obtener más información sobre los diferentes enfoques, vea [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Ejecutar herramientas de generación de perfiles con o sin el depurador).

![Generador de perfiles de rendimiento](../profiling/media/prof-tour-performance-profiler.png "Generador de perfiles de rendimiento")

Para abrir el Generador de perfiles de rendimiento, seleccione **Depurar / Generador de perfiles de rendimiento**.

La ventana le permitirá seleccionar varias herramientas de generación de perfiles en algunos escenarios. Las herramientas como Uso de CPU proporcionan datos complementarios que le pueden ayudar en el análisis.

## <a name="analyze-resource-consumption-xaml"></a>Análisis del consumo de recursos (XAML)

En las aplicaciones XAML (como las aplicaciones de WPF de escritorio de Windows y las aplicaciones para UWP), puede analizar el consumo de recursos mediante la herramienta Escala de tiempo de la aplicación. Por ejemplo, puede analizar el tiempo consumido por la aplicación en la preparación de marcos de la interfaz de usuario (diseño y presentación), la atención de solicitudes de red y de disco y escenarios como el inicio de la aplicación, carga de la página y cambio de tamaño de las ventanas. Para usar la herramienta, seleccione **Escala de tiempo de la aplicación** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario en el que sospecha que se produce un problema de consumo de recursos y, después, seleccione **Detener recolección** para generar el informe.

Los valores de framerate bajos en el gráfico **Rendimiento visual** podrían corresponderse con los problemas visuales que ve cuando se ejecuta la aplicación. De forma similar, los números elevados en el gráfico **Uso del subproceso de UI** podrían corresponderse con problemas en la capacidad de respuesta de la interfaz de usuario. En el informe, puede seleccionar un período de tiempo en el que sospecha que se produce un problema de rendimiento y, después, examinar las actividades detalladas del subproceso de interfaz de usuario en la vista Detalles de la escala de tiempo (panel inferior).

![Herramienta de generación de perfiles en la Escala de tiempo de la aplicación](../profiling/media/prof-tour-application-timeline.gif "Escala de tiempo de la aplicación en la guía de generación de perfiles")

En la vista Detalles de la escala de tiempo, encontrará información como el tipo de actividad (o el elemento de la interfaz de usuario implicado) junto con la duración de la actividad. Por ejemplo, en la ilustración, un evento de **Diseño** para un control de cuadrícula tarda 57,53 ms.

Para obtener más información, vea [Application Timeline](../profiling/application-timeline.md) (Escala de tiempo de la aplicación).

## <a name="analyze-gpu-usage-direct3d"></a>Análisis del uso de la GPU (Direct3D)

En las aplicaciones Direct3D (los componentes Direct3D deben estar en C++), puede examinar la actividad de la GPU y analizar problemas de rendimiento. Para obtener más información, vea [GPU Usage](../debugger/gpu-usage.md) (Uso de GPU). Para usar la herramienta, seleccione **Uso de GPU** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario del que le interesa generar un perfil y, después, seleccione **Detener recolección** para generar un informe.

Si elige un período de tiempo en los gráficos y selecciona **Ver detalles**, aparece una vista detallada en el panel inferior. En la vista detallada, puede examinar cuántas actividades se producen en cada CPU y GPU. Seleccione los eventos en el panel inferior para que aparezcan elementos emergentes en la escala de tiempo. Por ejemplo, seleccione el evento **Presente** para ver elementos emergentes de llamada **Presente**. (Las líneas de sincronización vertical de color gris claro se pueden usar como referencia para entender si alguna llamada **Presente** se ha perdido la sincronización vertical. Debe haber una llamada **Presente** entre cada dos sincronizaciones verticales para que la aplicación alcance constantemente los 60 FPS).

![Herramienta de generación de perfiles de uso de GPU](../profiling/media/prof-tour-gpu-usage.png "Diagnóstico de uso de GPU")

También puede usar los gráficos para determinar si hay cuellos de botella de rendimiento relacionados con la CPU o con la GPU.

## <a name="analyze-performance-javascript"></a>Análisis del rendimiento (JavaScript)

En el caso de las aplicaciones HTML universales de Windows, puede usar la herramienta Memoria de JavaScript y la herramienta Capacidad de respuesta de la IU HTML.

La herramienta Memoria de JavaScript es similar a la herramienta Uso de memoria disponible para otros tipos de aplicaciones. Puede usar esta herramienta para entender el uso de memoria y buscar fugas de memoria en la aplicación. Para obtener más información sobre la herramienta, vea [JavaScript Memory](../profiling/javascript-memory.md) (Memoria de JavaScript).

![Herramienta de generación de perfiles de Memoria de JavaScript](../profiling/media/diagjsmemory.png "Diagnóstico de Memoria de JavaScript")

Para diagnosticar la capacidad de respuesta de la interfaz de usuario, el tiempo de carga lento y las actualizaciones visuales lentas en aplicaciones HTML universales de Windows, use la herramienta Capacidad de respuesta de la IU HTML. El uso es similar al de la herramienta Escala de tiempo de la aplicación para otros tipos de aplicaciones. Para obtener más información, vea [HTML UI responsiveness](../profiling/html-ui-responsiveness.md) (Capacidad de respuesta de IU HTML).

![Herramienta de generación de perfiles de respuesta de UI de HTML](../profiling/media/diaghtmlresp.png "Diagnóstico de respuesta de HTML")

## <a name="analyze-network-usage-uwp"></a>Análisis del uso de la red (UWP)

En las aplicaciones UWP, puede analizar las operaciones de red realizadas mediante la API `Windows.Web.Http`. Esta herramienta puede ayudarle a resolver cuestiones como problemas de acceso y autenticación, uso incorrecto de la caché y rendimiento deficiente de visualización y descarga. Para usar la herramienta, seleccione **Red** en el Generador de perfiles de rendimiento y, después, elija **Iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Herramienta de generación de perfiles de Uso de red](../profiling/media/prof-tour-network-usage.png "Diagnóstico de Uso de red")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta de Uso de red](../profiling/media/prof-tour-network-usage-details.png "Detalles del diagnóstico de Uso de red")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).

## <a name="analyze-performance-legacy-tools"></a>Análisis de rendimiento (herramientas heredadas)

Si necesita características que no están actualmente presentes en las herramientas Uso de CPU o Uso de memoria, como la instrumentación, y ejecuta aplicaciones ASP.NET o de escritorio, puede usar el Explorador de rendimiento para la generación de perfiles. (No se admite en aplicaciones UWP). Para más información, vea [Explorador de rendimiento](../profiling/performance-explorer.md).

![Herramienta de Explorador de rendimiento](../profiling/media/prof-tour-performance-explorer.png "Explorador de rendimiento")

## <a name="which-tool-should-i-use"></a>¿Qué herramienta debo usar?  
En esta tabla se muestra una lista de las distintas herramientas que ofrece Visual Studio y los tipos de proyecto con los que las puede usar:
  
|Herramienta de rendimiento|Escritorio de Windows|Universales de Windows o de la Tienda|ASP.NET/ASP.NET Core|  
|----------------------|---------------------|------------------------------|-------------|  
|[Uso de memoria](../profiling/memory-usage.md)|sí|sí|sí|  
|[Uso de CPU](../profiling/cpu-usage.md)|sí|sí|sí (no para .NET Core/ASP.NET Core)|  
|[Uso de GPU](../debugger/gpu-usage.md)|sí|sí|no|  
|[Escala de tiempo de la aplicación](../profiling/application-timeline.md)|sí|sí|no|  
|[Sugerencias de rendimiento](../profiling/perftips.md)|sí|sí para XAML, no para HTML|sí|  
|[Explorador de rendimiento](../profiling/performance-explorer.md)|sí|no|sí (no para el núcleo de ASP.NET)|  
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET Enterprise|Solo .NET Enterprise|Solo .NET Enterprise|
|[Uso de red](../profiling/network-usage.md)|no|sí|no| 
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|no|sí para HTML, no para XAML|no|  
|[Memoria de JavaScript](../profiling/javascript-memory.md)|no|sí para HTML, no para XAML|no|  

## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)