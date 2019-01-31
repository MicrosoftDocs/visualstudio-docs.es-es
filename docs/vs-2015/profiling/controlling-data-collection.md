---
title: Controlar la recolección de datos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780952"
---
# <a name="controlling-data-collection"></a>Controlar la recolección de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permiten controlar cuándo se recopilan los datos de generación de perfiles durante una sesión de rendimiento y especificar las funciones de las que se van a generar perfiles. En esta sección se describe cómo iniciar y detener la recolección de datos desde el **Explorador de rendimiento** y las ventanas **Control de recolección de datos** y cómo limitar los objetos para los que se recopilan datos de generación de perfiles.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Iniciar y detener la generación de perfiles**: Puede iniciar la generación de perfiles de una aplicación cuando se inicie la aplicación, o puede asociar el generador de perfiles a un proceso que ya se esté ejecutando. Cuando la aplicación de destino esté en funcionamiento, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, cierre la aplicación de destino o desasocie el generador de perfiles de un proceso en ejecución.|-   [Cómo: Inicio y finalización de la recopilación de datos de rendimiento](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Cómo: Asociación y desasociación de las herramientas de rendimiento en los procesos en ejecución](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Cómo: Pausa y reanudación de la recopilación de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configurar la generación de perfiles de instrumentación para limitar los datos recopilados**: Puede usar las propiedades de configuración de la sesión de rendimiento para limitar los datos que se recopilan en las ejecuciones de generación de perfiles que emplean el método de instrumentación. Puede incluir o excluir archivos .dll, espacios de nombres, clases y funciones concretos. También puede excluir funciones que no cumplan el umbral de tamaño que especifique.|-   [Cómo: Limitación de la instrumentación a archivos DLL específicos](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Cómo: Limitación de la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Cómo: Exclusión o inclusión de funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)
