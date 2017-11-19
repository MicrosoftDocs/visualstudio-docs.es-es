---
title: "Eliminar un punto de interrupción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2789fd46942a9b54ca3d6efb082a6b21511969ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="deleting-a-breakpoint"></a>Eliminar un punto de interrupción
A continuación describe el proceso cuando se elimina un punto de interrupción pendiente:  
  
## <a name="deletion-process"></a>Proceso de eliminación  
 El Administrador de sesión de depuración (SDM) llama el [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para quitar el punto de interrupción pendiente y enlazados todos los puntos de interrupción enlazado de él.  
  
> [!NOTE]
>  También es posible eliminar un punto de interrupción enlazado mediante una llamada a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)