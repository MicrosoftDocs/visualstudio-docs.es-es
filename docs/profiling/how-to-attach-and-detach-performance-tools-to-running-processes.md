---
title: "C&#243;mo: Asociar y desasociar el generador de perfiles de los procesos en ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.attach"
helpviewer_keywords: 
  - "herramientas de rendimiento, asociar un proceso"
  - "herramientas de generación de perfiles, desasociar un proceso"
  - "herramientas de generación de perfiles, asociar un proceso"
  - "herramientas de rendimiento, desasociar un proceso"
  - "generador de perfiles"
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Asociar y desasociar el generador de perfiles de los procesos en ejecuci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El generador de perfiles puede utilizarse para asociarlo o desasociarlo de un proceso en ejecución con el fin de facilitar el muestreo y la recolección de los datos de rendimiento.  Puede utilizar este método para generar los perfiles de un proceso cuando desea evitar que se recopilen datos sobre el tiempo de carga de la aplicación, o bien, para supervisar el rendimiento de un proceso después de que alcance un estado determinado.  
  
> [!NOTE]
>  Los pasos siguientes se aplican a los procesos de asociación y desasociación desde el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Para obtener información sobre cómo utilizar las herramientas de línea de comandos, vea [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md).  Para obtener información acerca de cómo generar perfiles de los servicios, vea [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md).  
  
 Los procesos disponibles para la generación de perfiles dependen de los permisos de acceso de usuario establecidos por el administrador del equipo.  Por ejemplo, una cuenta de usuario puede tener permiso para cualquiera de las funciones siguientes:  
  
-   Características avanzadas de generación de perfiles, cuando el administrador ha configurado el controlador y el servicio que deben iniciarse.  
  
-   Generación de perfiles de muestreo solamente \(usuarios del dominio\).  
  
-   Denegación de acceso de todos los usuarios a la generación de perfiles.  
  
 Para obtener más información, vea [Generar perfiles y seguridad en Windows Vista](../profiling/profiling-and-windows-vista-security.md) y las opciones de ADMIN en [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Para asociar a un proceso en ejecución  
  
1.  En el menú **Analizar**, elija **Generador de perfiles** y, a continuación, haga clic en **Asociar\/Desasociar**.  
  
     – O bien –  
  
     En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Asociar\/Desasociar**.  
  
     Aparecerá el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre del proceso que desea adjuntar.  
  
3.  Haga clic en **Adjuntar**.  
  
### Para desasociar de un proceso en ejecución  
  
1.  En el menú **Analizar**, elija **Generador de perfiles** y, a continuación, haga clic en **Asociar\/Desasociar**.  
  
     – O bien –  
  
     En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Asociar\/Desasociar**.  
  
     Aparecerá el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre de imagen del que desea desasociar.  
  
3.  Haga clic en **Desasociar**.  
  
## Vea también  
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)   
 [Información general sobre las sesiones de rendimiento](../profiling/performance-session-overview.md)   
 [Cómo: Iniciar y finalizar generaciones de perfiles](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Generar perfiles y seguridad en Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)