---
title: Problemas de seguridad | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6807ea81d1898bfaf9c766e25e3c84c021c3aae5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799644"
---
# <a name="security-issues"></a>Problemas de seguridad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para depurar un programa con Visual Studio, los únicos permisos necesitados son los mismos que un desarrollador necesita para ejecutar el programa. Esto incluye la depuración remota para la mayoría de los casos (algunas situaciones que afectan a otros servicios, como Internet Information Services, pueden requerir un mayor nivel de permisos).  
  
 Mientras se está ejecutando Visual Studio, el Administrador de depuración del proceso (PDM) realiza el seguimiento de los procesos de depuración en el equipo local. De forma remota, un programa llamado msvsmon.exe se inicia el programador para controlar la depuración remota y que esté disponible el PDM. (Tenga en cuenta que msvsmon.exe no es un servicio y se debe iniciar manualmente para habilitar la depuración remota en ese equipo.) Cuando Visual Studio (msvsmon.exe) no se ejecuten, no hay procesos se siguen para la depuración.  
  
 Esto significa que un desarrollador puede depurar programas que se inició sin ningún permiso especial. El desarrollador incluso puede depurar procesos iniciados por otra persona si esa otra persona es un miembro del mismo grupo de seguridad. Y para habilitar la depuración remota, es necesario solo para copiar el necesario archivos en el servidor remoto del equipo e iniciar msvsmon.exe (consulte [establecer las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obtener más detalles).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md)   
 [Configurar las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)

