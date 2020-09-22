---
title: Eliminar un punto de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842803"
---
# <a name="deleting-a-breakpoint"></a>Eliminación de un punto de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se describe el proceso al eliminar un punto de interrupción pendiente:  
  
## <a name="deletion-process"></a>Proceso de eliminación  
 El administrador de depuración de sesión (SDM) llama al método [IDebugPendingBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados enlazados a él.  
  
> [!NOTE]
> Un solo punto de interrupción enlazado también puede eliminarse mediante una llamada a [IDebugBoundBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
