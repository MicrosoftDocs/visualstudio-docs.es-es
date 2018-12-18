---
title: Configurar sesiones de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e00c31643a5f894612daa24d4a271856d8e21f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853446"
---
# <a name="configure-performance-sessions"></a>Configurar sesiones de rendimiento
Mediante el uso de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede recopilar una gran variedad de datos de rendimiento para un gran número de tipos de aplicaciones. En esta sección se muestra cómo utilizar las propiedades del Asistente de rendimiento, las propiedades de la sesión de rendimiento y el binario de destino para configurar las herramientas de generación de perfiles para recopilar los datos que le interesen. Las propiedades de configuración de las herramientas de generación de perfiles también pueden emplearse para controlar la cantidad de datos recopilados en una ejecución de generación de perfiles. Para más información, vea [Control de la recopilación de datos](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  En muchos casos, utilizar las propiedades predeterminadas del Asistente de rendimiento es una forma eficaz de recopilar datos de generación de perfiles. Para más información, vea [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md) e [Introducción](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Tareas comunes
  
| Tarea | Contenido relacionado |
| - | - |
| **Establecer las opciones de generación de perfiles básicas:** debe configurar [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] para utilizar el servidor de símbolos de Microsoft. Esto asegurará que tiene acceso a los símbolos, como los nombres de las funciones y los parámetros, para la versión actual de Windows y otras aplicaciones de Microsoft. También puede especificar otras opciones generales antes de iniciar una sesión de generación de perfiles, como los permisos de sistema para las herramientas de generación de perfiles y los nombres de los archivos de datos de generación de perfiles. | -   [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Cómo: Serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)<br />-   [Cómo: Establecer la sesión actual](../profiling/how-to-set-the-current-session.md)<br />-   [Cómo: Establecer permisos](../profiling/how-to-set-permissions.md)<br />-   [Cómo: establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Especificar los datos que quiere recopilar:** los procedimientos que se utilizan para configurar una sesión de generación de perfiles dependen del tipo de aplicación de destino de la que se quiere generar el perfil y del tipo de datos de rendimiento que se van a recopilar. | -   [Cómo: Elegir métodos de recopilación](../profiling/how-to-choose-collection-methods.md)<br />-   [Recopilación de estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Recopilación de datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Cómo: Generar perfiles de código de JavaScript en páginas web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Recopilación de datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Recopilación de datos de rendimiento adicionales](../profiling/collecting-additional-performance-data.md) |
| **Establecer opciones de configuración avanzada:** al generar perfiles de aplicaciones .NET Framework que cargan varias versiones de Common Language Run-time (CLR), puede especificar de qué versión se va a generar el perfil. Cuando tenga varios archivos .exe en una sesión de rendimiento, puede establecer el orden de inicio de los archivos binarios. | -   [Cómo: Especificar runtime de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Cómo: Especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md) |
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Control de la recopilación de datos](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)