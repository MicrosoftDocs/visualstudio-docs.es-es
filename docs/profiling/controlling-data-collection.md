---
title: "Controlar recolecciones de datos en las Herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tareas avanzadas para herramientas de generación de perfiles"
  - "herramientas de generación de perfiles, tareas avanzadas"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Controlar recolecciones de datos en las Herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permiten controlar cuándo se recopilan los datos de generación de perfiles durante una sesión de rendimiento y especificar las funciones de las que se van a generar perfiles.  En esta sección se describe cómo iniciar y detener la recolección de datos desde el **Explorador de rendimiento** y las ventanas **Control de recolección de datos** y cómo limitar los objetos para los que se recopilan datos de generación de perfiles.  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Iniciar y detener la generación de perfiles:** puede iniciar la generación de perfiles de una aplicación cuando se inicie la aplicación, o puede adjuntar el generador de perfiles a un proceso que ya se esté ejecutando.  Cuando la aplicación de destino esté en funcionamiento, puede pausar y reanudar la recolección de datos.  Para finalizar una sesión de generación de perfiles, cierre la aplicación de destino o desasocie el generador de perfiles de un proceso en ejecución.|-   [Cómo: Iniciar y finalizar generaciones de perfiles](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Cómo: Asociar y desasociar el generador de perfiles de los procesos en ejecución](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Cómo: Pausar y reanudar la generación de perfiles](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)|  
|**Configurar la generación de perfiles de instrumentación para limitar los datos recabados:** puede utilizar las propiedades de configuración de la sesión de rendimiento para limitar los datos que se recopilan en las ejecuciones de generación de perfiles que utilizan el método de instrumentación.  Puede incluir o excluir archivos .dll, espacios de nombres, clases y funciones concretos.  También puede excluir funciones que no cumplan el umbral de tamaño que especifique.|-   [Cómo: Limitar la instrumentación a archivos DLL específicos](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Cómo: Excluir o incluir funciones cortas en la instrumentación](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)|  
  
## Secciones relacionadas  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)  
  
## Vea también  
 [Uso de las herramientas de generación de perfiles](../profiling/performance-explorer.md)