---
title: Terminación y separado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176673"
---
# <a name="termination-and-detaching"></a>Terminación y desasociación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación describe la finalización normal.  
  
## <a name="discussion"></a>Discusión  
 Después de la [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continúa la interfaz, si hay no hay puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar, el programa que se está depurando se ejecutará hasta su finalización. Se trata de una finalización normal.  
  
 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la finalización normal. Esto requiere la implementación de la [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
