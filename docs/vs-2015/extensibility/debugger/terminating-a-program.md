---
title: Terminación de un programa | Microsoft Docs
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
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e15fa5746b5cd7fae66574ec0d318cad1184cfdd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861207"
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

