---
title: Problemas de seguridad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704418"
---
# <a name="security-issues"></a>Problemas de seguridad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para depurar un programa con Visual Studio, los únicos permisos necesarios son los mismos que un desarrollador necesita para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones (algunas situaciones en las que intervienen otros servicios, como Internet Information Services, pueden requerir un nivel de permisos superior).  
  
 Mientras Visual Studio se está ejecutando, el administrador de depuración de proceso (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, el desarrollador inicia un programa llamado msvsmon.exe para controlar la depuración remota y hacer que el PDM esté disponible. (Tenga en cuenta que msvsmon.exe no es un servicio y debe iniciarse manualmente para habilitar la depuración remota en ese equipo). Cuando Visual Studio (o msvsmon.exe) no se está ejecutando, no se realiza el seguimiento de ningún proceso para la depuración.  
  
 Esto significa que un desarrollador puede depurar programas que inició sin permisos especiales. El desarrollador puede incluso depurar los procesos iniciados por otro usuario si esa persona es miembro del mismo grupo de seguridad. Y para habilitar la depuración remota, solo es necesario copiar los archivos necesarios en el equipo remoto e iniciar msvsmon.exe (consulte [configuración del herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obtener más detalles).  
  
## <a name="see-also"></a>Consulte también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Procesar el administrador de depuración](../../extensibility/debugger/process-debug-manager.md)   
 [Configurar las herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
