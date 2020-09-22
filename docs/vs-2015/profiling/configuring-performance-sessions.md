---
title: Configurar sesiones de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d67801cedded1ccf66544e21257866feda828e31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842350"
---
# <a name="configuring-performance-sessions"></a>Configurar sesiones de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante el uso de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede recopilar una gran variedad de datos de rendimiento para un gran número de tipos de aplicaciones. En esta sección se muestra cómo utilizar las propiedades del Asistente de rendimiento, las propiedades de la sesión de rendimiento y el binario de destino para configurar las herramientas de generación de perfiles para recopilar los datos que le interesen. Las propiedades de configuración de las herramientas de generación de perfiles también pueden emplearse para controlar la cantidad de datos recopilados en una ejecución de generación de perfiles. Para obtener más información, consulte [Controlar la recolección de datos](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
> En muchos casos, utilizar las propiedades predeterminadas del Asistente de rendimiento es una forma eficaz de recopilar datos de generación de perfiles. Para obtener más información, consulte [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md) y [Introducción](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Establecer las opciones de generación de perfiles básicas:** debe configurar [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] para utilizar el servidor de símbolos de Microsoft. Esto asegurará que tiene acceso a los símbolos, como los nombres de las funciones y los parámetros, para la versión actual de Windows y otras aplicaciones de Microsoft. También puede especificar otras opciones generales antes de iniciar una sesión de generación de perfiles, como los permisos de sistema para las herramientas de generación de perfiles y los nombres de los archivos de datos de generación de perfiles.|-   [Cómo: hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Cómo: serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)<br />-   [Cómo: establecer la sesión actual](../profiling/how-to-set-the-current-session.md)<br />-   [Cómo: establecer permisos](../profiling/how-to-set-permissions.md)<br />-   [Cómo: Establecimiento de opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Especificar los datos que quiere recopilar:** los procedimientos que se utilizan para configurar una sesión de generación de perfiles dependen del tipo de aplicación de destino de la que se quiere generar el perfil y del tipo de datos de rendimiento que se van a recopilar.|-   [Cómo: elegir métodos de colección](../profiling/how-to-choose-collection-methods.md)<br />-   [Recopilar estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Cómo: generar perfiles de código JavaScript en páginas web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Recopilar datos de simultaneidad de procesos y subprocesos](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Recopilación de datos de rendimiento adicionales](../profiling/collecting-additional-performance-data.md)|  
|**Establecer opciones de configuración avanzada:** al generar perfiles de aplicaciones .NET Framework que cargan varias versiones de Common Language Run-time (CLR), puede especificar de qué versión se va a generar el perfil. Cuando tenga varios archivos .exe en una sesión de rendimiento, puede establecer el orden de inicio de los archivos binarios.|-   [Cómo: especificar el tiempo de ejecución de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Cómo: especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Consulte también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)
