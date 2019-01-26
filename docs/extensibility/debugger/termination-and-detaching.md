---
title: Terminación y separado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efaeb409d49c31e47f66bb5d593d1da6a3d97919
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971564"
---
# <a name="termination-and-detaching"></a>Terminación y separado
La siguiente sección describe la finalización normal.  
  
## <a name="discussion"></a>Explicación  
 Después de la [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continúa la interfaz, si hay no hay puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar, el programa que se está depurando se ejecuta hasta su finalización. Este proceso es la finalización normal.  
  
 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la finalización normal. Terminación normal debe ejecutarse el [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)