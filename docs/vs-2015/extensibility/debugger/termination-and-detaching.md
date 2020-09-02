---
title: Terminación y desasociación | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176673"
---
# <a name="termination-and-detaching"></a>Terminación y desasociación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se describe la terminación normal.  
  
## <a name="discussion"></a>Debate  
 Después de que la interfaz [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continúe, si no hay puntos de interrupción, excepciones, errores en tiempo de ejecución o bucles infinitos en la aplicación que se va a depurar, el programa que se está depurando se ejecutará hasta completarse. Esta es la terminación normal.  
  
 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la terminación normal. Esto requiere la implementación del método [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
