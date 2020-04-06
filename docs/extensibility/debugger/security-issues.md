---
title: Problemas de seguridad ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713050"
---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa mediante Visual Studio, los únicos permisos necesarios son los mismos que un desarrollador necesita para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones. Algunas situaciones, que implican otros servicios, como el Servicio de Internet Information Service, pueden requerir un mayor nivel de permisos.

 Mientras se ejecuta Visual Studio, el Administrador de depuración de procesos (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, el desarrollador inicia un programa llamado *msvsmon.exe* para controlar la depuración remota y hacer que PDM esté disponible. (*msvsmon.exe* no es un servicio y debe iniciarse manualmente para habilitar la depuración remota en ese equipo.) Cuando Visual Studio (o *msvsmon.exe*) no se está ejecutando, no se realiza un seguimiento de ningún proceso para la depuración.

 Un desarrollador puede depurar programas que iniciaron sin permisos especiales. El desarrollador puede incluso depurar procesos iniciados por otra persona si esa otra persona es miembro del mismo grupo de seguridad. Y, para habilitar la depuración remota, sólo es necesario copiar los archivos necesarios en el equipo remoto e iniciar *msvsmon.exe*. Para obtener más información, consulte [Depuración remota](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md)
- [Depuración remota](../../debugger/remote-debugging.md)
