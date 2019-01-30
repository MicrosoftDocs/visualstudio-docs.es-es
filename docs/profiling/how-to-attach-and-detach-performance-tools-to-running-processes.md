---
title: Asociación de herramientas de rendimiento a procesos en ejecución
ms.custom: seodec18
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d735127be1b8a412395be8d19321deb8d589be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992495"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Procedimiento Asociar y desasociar las herramientas de rendimiento en los procesos en ejecución
El generador de perfiles puede utilizarse para asociar o desasociar un proceso en ejecución a fin de facilitar el muestreo y la recolección de los datos de rendimiento. Puede utilizar este método para generar perfiles de un proceso cuando quiera evitar que se recopilen datos sobre el tiempo de carga de la aplicación o supervisar el rendimiento de un proceso después de que alcance un estado determinado.  
  
> [!NOTE]
>  Los pasos siguientes se aplican a asociar y desasociar procesos desde el entorno de desarrollo integrado (IDE) de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Para obtener información sobre cómo utilizar las herramientas de la línea de comandos, vea [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md). Para obtener información sobre cómo generar perfiles para servicios, vea [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md).  
  
 Los procesos que están disponibles para generar perfiles dependen de los permisos de acceso de usuario establecidos por un administrador del equipo. Por ejemplo, una cuenta de usuario puede tener permiso para cualquiera de las siguientes acciones:  
  
- Características avanzadas de generación de perfiles, cuando el administrador ha configurado el controlador y el servicio para que se inicien.  
  
- Solo para la generación de perfiles de ejemplo (usuarios de dominio).  
  
- Denegar el acceso a la generación de perfiles a todo el mundo.  
  
  Para obtener más información, vea [Generación de perfiles y seguridad de Windows Vista](../profiling/profiling-and-windows-vista-security.md) y las opciones de administración de [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Para asociar a un proceso en ejecución  
  
1.  En el menú **Depurar**, vaya a **Generador de perfiles**, a **Explorador de rendimiento** y después haga clic en **Adjuntar**.    
  
     Se muestra el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre del proceso al que quiera asociar.  
  
3.  Haga clic en **Asociar**.  
  
### <a name="to-detach-from-a-running-process"></a>Desasociar de un proceso en ejecución  
  
1.  En el menú **Depurar**, vaya a **Generador de perfiles**, a **Explorador de rendimiento** y después haga clic en **Desasociar**. 
  
     Se muestra el cuadro de diálogo **Asociar generador de perfiles al proceso**.  
  
2.  Haga clic en el nombre de la imagen que quiera desasociar.  
  
3.  Haga clic en **Desasociar**.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Información general sobre las sesiones de rendimiento](../profiling/performance-session-overview.md)   
 [Cómo: Iniciar y finalizar la recopilación de datos de rendimiento](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Generación de perfiles y seguridad en Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)