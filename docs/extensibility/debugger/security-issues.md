---
title: Problemas de seguridad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd4d07721f202169ca0689882ac1a41045a4d61
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252328"
---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa con Visual Studio, los únicos permisos necesitados son los mismos que un desarrollador necesita para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones. Algunas situaciones, que afectan a otros servicios, como Internet Information Services, pueden requerir un mayor nivel de permisos.  
  
 Mientras se está ejecutando Visual Studio, el Administrador de depuración del proceso (PDM) realiza el seguimiento de los procesos de depuración en el equipo local. De forma remota, un programa llamado *msvsmon.exe* se inicia el programador para controlar la depuración remota y que esté disponible el PDM. (*msvsmon.exe* no es un servicio y se debe iniciar manualmente para habilitar la depuración remota en ese equipo.) Cuando Visual Studio (o *msvsmon.exe*) es no se está ejecutando, no hay ningún proceso se realiza un seguimiento de depuración.  
  
 Un desarrollador puede depurar programas que inició sin ningún permiso especial. El desarrollador incluso puede depurar procesos iniciados por otra persona si esa otra persona es un miembro del mismo grupo de seguridad. Y, para habilitar la depuración remota, es necesario solo copiar los archivos necesarios en el equipo remoto e iniciar *msvsmon.exe*. Para obtener más información, consulte [depuración remota](../../debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md)   
 [Depuración remota](../../debugger/remote-debugging.md)
