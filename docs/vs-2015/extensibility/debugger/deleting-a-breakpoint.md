---
title: Eliminar un punto de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18b88cc55a4c641e56c062356a9f74c2224835a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578384"
---
# <a name="deleting-a-breakpoint"></a>Eliminación de un punto de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [eliminando un punto de interrupción](https://docs.microsoft.com/visualstudio/extensibility/debugger/deleting-a-breakpoint).  
  
El siguiente describe el proceso al eliminar un punto de interrupción pendiente:  
  
## <a name="deletion-process"></a>Proceso de eliminación  
 El Administrador de depuración de la sesión (SDM) llama a la [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para quitar el punto de interrupción pendiente y enlazados todos los puntos de interrupción enlazado de él.  
  
> [!NOTE]
>  También se puede eliminar un punto de interrupción enlazado mediante una llamada a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)

