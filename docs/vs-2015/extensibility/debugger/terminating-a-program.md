---
title: Finalización de un programa | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421868"
---
# <a name="terminating-a-program"></a>Terminación de un programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se proporciona una descripción de la terminación de un solo programa con un subproceso.  
  
## <a name="termination-process"></a>Proceso de finalización  
  
1. El DE envía un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido.  
  
2. El DE envía un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido.  
  
   El IDE entra en el modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa del puerto.  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
