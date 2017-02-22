---
title: "Configurar sesiones de rendimiento para las Herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tareas comunes, rendimiento"
  - "tareas comunes, herramientas de generación de perfiles"
  - "herramientas de generación de perfiles, tareas comunes"
  - "rendimiento, recopilación de datos"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configurar sesiones de rendimiento para las Herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizando las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede recopilar una amplia variedad de datos de rendimiento para un gran número de tipos de aplicación.  En esta sección se muestra cómo utilizar el **Asistente de rendimiento**, las propiedades de la sesión de rendimiento y el binario de destino para configurar las herramientas de generación de perfiles con el fin de recopilar los datos que le interesan.  Las propiedades de configuración de las herramientas de generación de perfiles también pueden utilizarse para controlar la cantidad de datos recopilados en una generación de perfiles.  Para obtener más información, vea [Controlar la recolección de datos](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  En muchos casos, utilizar las propiedades predeterminadas del Asistente de rendimiento es una manera eficiente de recopilar datos de generación de perfiles.  Para obtener más información, vea [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md) y [Introducción](../profiling/getting-started-with-performance-tools.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Establezca las opciones básicas de generación de perfiles:** debe configurar [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] para utilizar el servidor de símbolos de Microsoft.  Así se asegurará de tener acceso a los símbolos, tales como nombres de función y de parámetro, para la versión actual de Windows y otras aplicaciones de Microsoft.  También puede especificar otras opciones generales antes de que se inicie una sesión de generación de perfiles, tales como los permisos del sistema para las herramientas de generación de perfiles y los nombres de los archivos de datos de generación de perfiles.|-   [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Cómo: Serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)<br />-   [Cómo: Establecer la sesión de generación de perfiles actual](../Topic/How%20to:%20Set%20the%20Current%20Session.md)<br />-   [Cómo: Establecer los permisos de generación de perfiles](../profiling/how-to-set-permissions.md)<br />-   [Cómo: Establecer opciones de nombre de archivo de datos de generación de perfiles](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Especifique los datos que desea recopilar:** los procedimientos que utilice para configurar una sesión de generación de perfiles dependen del tipo de aplicación de destino que desee perfilar y del tipo de datos de rendimiento que desee recopilar.|-   [Cómo: Elegir métodos de recolección](../profiling/how-to-choose-collection-methods.md)<br />-   [Recopilar estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Recolección de datos de control de tiempo detallados utilizando instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Cómo: Generar perfiles de código de JavaScript \(ECMA\) en páginas web](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [Recopilar datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Recopilar datos de rendimiento adicionales](../profiling/collecting-additional-performance-data.md)|  
|**Establezca las opciones de configuración avanzadas:** al generar perfiles para aplicaciones .NET Framework que carguen varias versiones del Common Language Runtime \(CLR\), puede especificar para qué versión desea realizar la generación de perfiles.  Cuando tenga varios archivos .exe en una sesión de rendimiento, puede establecer el orden del inicio de los binarios.|-   [Cómo: Especificar el runtime de .NET Framework para la generación de perfiles en escenarios en paralelo](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)<br />-   [Cómo: Especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## Secciones relacionadas  
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)  
  
## Vea también  
 [Uso de las herramientas de generación de perfiles](../profiling/performance-explorer.md)