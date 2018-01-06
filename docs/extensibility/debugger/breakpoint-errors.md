---
title: "Errores de punto de interrupción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd9347290199ce695f7b2f42733ad8e5d108ac0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoint-errors"></a>Errores de punto de interrupción
Los siguientes elementos describen el proceso cuando un punto de interrupción intenta enlazar al código, pero se produce un error:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Solución de problemas de un Error de punto de interrupción  
  
1.  El motor de depuración (Alemania) envía una [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) para el Administrador de sesión de depuración (SDM).  
  
2.  Las llamadas SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) para obtener el punto de interrupción de error.  
  
3.  Las llamadas SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obtener el punto de interrupción pendiente desde el que se originó el punto de interrupción de error.  
  
4.  Las llamadas SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obtener el motivo por qué el punto de interrupción de error no se pudo enlazar.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)