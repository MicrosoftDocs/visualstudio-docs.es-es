---
title: Problemas de seguridad | Microsoft Docs
description: Obtenga información sobre los permisos necesarios para depurar un programa con Visual Studio, incluida la depuración remota y las situaciones en las que participan otros servicios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1994a4a95d005edf4a71df3a1bb899522ecec137
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070432"
---
# <a name="security-issues"></a>Problemas de seguridad
Para depurar un programa con Visual Studio, los únicos permisos necesarios son los mismos que requiere un programador para ejecutar el programa. Esto incluye la depuración remota para la mayoría de las situaciones. Algunas situaciones, que implican otros servicios, como Internet Information Services, pueden requerir un nivel más alto de permisos.

 Mientras Visual Studio se está ejecutando, el administrador de depuración de proceso (PDM) realiza un seguimiento de los procesos de depuración en el equipo local. De forma remota, el desarrollador inicia un programa llamado *msvsmon.exe* para controlar la depuración remota y hacer que el PDM esté disponible. (*msvsmon.exe* no es un servicio y debe iniciarse manualmente para habilitar la depuración remota en ese equipo). Cuando Visual Studio (o *msvsmon.exe*) no se está ejecutando, no se realiza el seguimiento de ningún proceso para la depuración.

 Un programador puede depurar programas que han iniciado sin permisos especiales. El desarrollador puede incluso depurar los procesos iniciados por otro usuario si esa persona es miembro del mismo grupo de seguridad. Y, para habilitar la depuración remota, solo es necesario copiar los archivos necesarios en el equipo remoto e iniciar *msvsmon.exe*. Para obtener más información, vea [Depuración remota](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Consulte también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Procesar el administrador de depuración](../../extensibility/debugger/process-debug-manager.md)
- [Depuración remota](../../debugger/remote-debugging.md)
