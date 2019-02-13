---
title: Procedimiento Adjuntar y separar herramientas de rendimiento de los procesos en ejecución | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2357993f6f0d814bc2383564cafe16bb2e21225a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762440"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Cómo: Asociar y desasociar las herramientas de rendimiento de los procesos en ejecución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El generador de perfiles puede utilizarse para asociar o desasociar un proceso en ejecución a fin de facilitar el muestreo y la recolección de los datos de rendimiento. Puede utilizar este método para generar perfiles de un proceso cuando quiera evitar que se recopilen datos sobre el tiempo de carga de la aplicación o supervisar el rendimiento de un proceso después de que alcance un estado determinado.  
  
> [!NOTE]
>  Los pasos siguientes se aplican a asociar y desasociar procesos desde el entorno de desarrollo integrado (IDE) de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Para obtener información sobre cómo utilizar las herramientas de la línea de comandos, consulte [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md). Para obtener información sobre cómo generar perfiles para servicios, consulte [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md).  
  
 Los procesos que están disponibles para generar perfiles dependen de los permisos de acceso de usuario establecidos por un administrador del equipo. Por ejemplo, una cuenta de usuario puede tener permiso para cualquiera de las siguientes acciones:  
  
- Características avanzadas de generación de perfiles, cuando el administrador ha configurado el controlador y el servicio para que se inicien.  
  
- Solo para la generación de perfiles de ejemplo (usuarios de dominio).  
  
- Denegar el acceso a la generación de perfiles a todo el mundo.  
  
  Para obtener más información, consulte [Generación de perfiles y seguridad de Windows Vista](../profiling/profiling-and-windows-vista-security.md) y las opciones de administración de [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Para asociar a un proceso en ejecución  
  
1.  En el menú **Analizar**, seleccione **Generador de perfiles** y, después, haga clic en **Asociar/desasociar**.  
  
     \- o -  
  
     En el **Explorador de rendimiento**, haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Asociar/desasociar**.  
  
     Se muestra el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre del proceso al que quiera asociar.  
  
3.  Haga clic en **Asociar**.  
  
### <a name="to-detach-from-a-running-process"></a>Desasociar de un proceso en ejecución  
  
1.  En el menú **Analizar**, seleccione **Generador de perfiles** y, después, haga clic en **Asociar/desasociar**.  
  
     \- o -  
  
     En el **Explorador de rendimiento**, haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Asociar/desasociar**.  
  
     Se muestra el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre de la imagen que quiera desasociar.  
  
3.  Haga clic en **Desasociar**.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Información general sobre la sesión de rendimiento](../profiling/performance-session-overview.md)   
 [Cómo: Iniciar y finalizar la recopilación de datos de rendimiento](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Generación de perfiles y seguridad de Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
