---
title: Problemas de seguridad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa con Visual Studio, los permisos necesitados son los mismos que los programadores necesitan para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones (algunas situaciones que afectan a otros servicios, como el servicio de información de Internet, pueden requerir un mayor nivel de permisos).  
  
 Mientras se ejecuta Visual Studio, el Administrador de depuración del proceso (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, un programa llamado msvsmon.exe se inicia el programador para controlar la depuración remota y disponer de PDM. (Observe que msvsmon.exe no es un servicio y se debe iniciar manualmente para habilitar la depuración remota en el equipo). Cuando Visual Studio (msvsmon.exe) no se ejecuten, no hay procesos se realiza el seguimiento de depuración.  
  
 Esto significa que un desarrollador puede depurar programas que se inició sin ningún permiso especial. El desarrollador incluso puede depurar procesos iniciados por otra persona si esa otra persona es un miembro del mismo grupo de seguridad. Y para habilitar la depuración remota, es necesario sólo para copiar el necesario archivos en el equipo remoto del equipo e iniciar msvsmon.exe (consulte [depuración remota](../../debugger/remote-debugging.md) para obtener más detalles).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Administrador de depuración del proceso](../../extensibility/debugger/process-debug-manager.md)   
 [Depuración remota](../../debugger/remote-debugging.md)
