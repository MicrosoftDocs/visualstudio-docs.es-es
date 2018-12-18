---
title: Controlar la recolección de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8022dd8fdd480e4bc545923eeb96d64f16ed9a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803427"
---
# <a name="controlling-data-collection"></a>Controlar la recolección de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permiten controlar cuándo se recopilan los datos de generación de perfiles durante una sesión de rendimiento y especificar las funciones de las que se van a generar perfiles. En esta sección se describe cómo iniciar y detener la recolección de datos desde el **Explorador de rendimiento** y las ventanas **Control de recolección de datos** y cómo limitar los objetos para los que se recopilan datos de generación de perfiles.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Iniciar y detener la generación de perfiles:** puede iniciar la generación de perfiles de una aplicación cuando se inicie la aplicación, o puede adjuntar el generador de perfiles a un proceso que ya se esté ejecutando. Cuando la aplicación de destino esté en funcionamiento, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, cierre la aplicación de destino o desasocie el generador de perfiles de un proceso en ejecución.|-   [Cómo: Iniciar y finalizar la recopilación de datos de rendimiento](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Cómo: Adjuntar y separar las herramientas de rendimiento de los procesos en ejecución](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Cómo: Pausar y reanudar la recopilación de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configurar la generación de perfiles de instrumentación para limitar los datos recopilados:** puede utilizar las propiedades de configuración de la sesión de rendimiento para limitar los datos que se recopilan en las ejecuciones de generación de perfiles que utilizan el método de instrumentación. Puede incluir o excluir archivos .dll, espacios de nombres, clases y funciones concretos. También puede excluir funciones que no cumplan el umbral de tamaño que especifique.|-   [Cómo: Limitar la instrumentación a archivos DLL específicos](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Cómo: Excluir o incluir funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)



