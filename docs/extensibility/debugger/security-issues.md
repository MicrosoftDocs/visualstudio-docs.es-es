---
title: Problemas de seguridad | Documentos de Microsoft
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
ms.openlocfilehash: d45ebd8c4d80b84749838c2034d72159c9e39627
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126902"
---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa con Visual Studio, los permisos necesitados son los mismos que un desarrollador debe ejecutar el programa. Esto incluye la depuración remota para la mayoría de los casos (algunas situaciones que afectan a otros servicios, como Internet Information Services, pueden requerir un mayor nivel de permisos).  
  
 Mientras se está ejecutando Visual Studio, el Administrador de depuración de procesos (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, se inicia un programa llamado msvsmon.exe por el programador para controlar la depuración remota y que esté disponible el PDM. (Tenga en cuenta que msvsmon.exe no es un servicio y se debe iniciar manualmente para habilitar la depuración remota en ese equipo.) Cuando Visual Studio (msvsmon.exe) no se ejecuten, no se realiza el seguimiento de ningún proceso para la depuración.  
  
 Esto significa que un desarrollador puede depurar programas que se inició sin ningún permiso especial. El desarrollador incluso puede depurar procesos iniciados por otra persona si esa otra persona es un miembro del mismo grupo de seguridad. Y para habilitar la depuración remota, es necesario solo para copiar las necesarias archivos a la instancia remota del equipo e iniciar msvsmon.exe (vea [depuración remota](../../debugger/remote-debugging.md) para obtener más detalles).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md)   
 [Depuración remota](../../debugger/remote-debugging.md)