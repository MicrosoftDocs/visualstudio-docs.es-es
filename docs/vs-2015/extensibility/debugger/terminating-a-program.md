---
title: Terminación de un programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988599"
---
# <a name="terminating-a-program"></a>Terminación de un programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La siguiente es una descripción de la finalización de un programa con un subproceso único.  
  
## <a name="termination-process"></a>Proceso de finalización  
  
1. Los envíos DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con válido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Los envíos DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con válido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   El IDE entra en modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa desde el puerto.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
