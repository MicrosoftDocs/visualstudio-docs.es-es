---
title: Errores de punto de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b08b9bee82a2505411be95ef2e6634e7897c15ec
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153766"
---
# <a name="breakpoint-errors"></a>Errores de punto de interrupción
Siguiente describe el proceso cuando un punto de interrupción intenta enlazar al código, pero se produce un error.  
  
## <a name="troubleshoot-a-breakpoint-error"></a>Solucionar un error de punto de interrupción  
  
1.  El motor de depuración (DE) envía un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) el Administrador de depuración de la sesión (SDM).  
  
2.  Las llamadas SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) para obtener el punto de interrupción de error.  
  
3.  Las llamadas SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obtener el punto de interrupción pendiente desde la que se originó el punto de interrupción de error.  
  
4.  Las llamadas SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obtener el motivo de error para enlazar el punto de interrupción de error.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)