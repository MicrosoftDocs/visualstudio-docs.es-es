---
title: Problemas de seguridad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713050"
---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa con Visual Studio, los únicos permisos necesarios son los mismos que requiere un programador para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones. Algunas situaciones, que implican otros servicios, como Internet Information Services, pueden requerir un nivel más alto de permisos.

 Mientras Visual Studio se está ejecutando, el administrador de depuración de proceso (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, el desarrollador inicia un programa llamado *msvsmon.exe* para controlar la depuración remota y hacer que el PDM esté disponible. (*msvsmon.exe* no es un servicio y debe iniciarse manualmente para habilitar la depuración remota en ese equipo). Cuando Visual Studio (o *msvsmon.exe*) no se está ejecutando, no se realiza el seguimiento de ningún proceso para la depuración.

 Un programador puede depurar programas que han iniciado sin permisos especiales. El desarrollador puede incluso depurar los procesos iniciados por otro usuario si esa persona es miembro del mismo grupo de seguridad. Y, para habilitar la depuración remota, solo es necesario copiar los archivos necesarios en el equipo remoto e iniciar *msvsmon.exe*. Para obtener más información, vea [Depuración remota](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Procesar el administrador de depuración](../../extensibility/debugger/process-debug-manager.md)
- [Depuración remota](../../debugger/remote-debugging.md)
