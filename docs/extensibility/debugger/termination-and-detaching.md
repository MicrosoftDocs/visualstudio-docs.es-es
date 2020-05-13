---
title: Terminación y desvinculación ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712491"
---
# <a name="termination-and-detaching"></a>Terminación y desmontaje
En la siguiente sección se describe la terminación normal.

## <a name="discussion"></a>Discusión
 Después de que el [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaz continúa, si no hay puntos de interrupción, excepciones, errores en tiempo de ejecución o bucles infinitos en la aplicación que se va a depurar, el programa que se está depurando se ejecuta hasta su finalización. Este proceso es una terminación normal.

 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la terminación normal. La terminación normal requiere ejecutar el [método IDebugProgramDestroyEvent2::GetExitCode.](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)

## <a name="see-also"></a>Vea también
- [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
