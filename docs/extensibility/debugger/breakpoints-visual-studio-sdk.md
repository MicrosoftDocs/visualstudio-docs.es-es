---
title: Los puntos de interrupción (SDK de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2898a78971eaf20abe89274a1492afb343edfbb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919400"
---
# <a name="breakpoints-visual-studio-sdk"></a>Puntos de interrupción (Visual Studio SDK)
Hay tres tipos de puntos de interrupción: pendientes enlazados y error.  
  
 **Un punto de interrupción:**  
  
- Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o más contextos de código en uno o más programas. Cada vez que un programa que se está depurando código causa para cargar, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si pueden estar limitados.  
  
   Un punto de interrupción pendiente propio nunca se enlaza al código, pero en su lugar recopila y se dice que contienen todos los puntos de interrupción enlazados que genera.  
  
- Se representa mediante un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.  
  
  **Un punto de interrupción enlazado:**  
  
- Es una abstracción para un punto de interrupción asociada o enlazada a un contexto de código único. Cada punto de interrupción enlazado se genera en respuesta a un punto de interrupción pendiente. Un punto de interrupción pendiente sin embargo, puede generar más de un punto de interrupción enlazado.  
  
   Cuando se descarga código, un punto de interrupción enlazado puede independientes y se descartan.  
  
- Se representa mediante un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.  
  
  **Un punto de interrupción de error:**  
  
- Es una abstracción para describir un error al intentar enlazar un punto de interrupción pendiente a un contexto de código. Un punto de interrupción de error describe un error en la ubicación o en la propia expresión de punto de interrupción. Para obtener más información, consulte [enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md).  
  
   El error de punto de interrupción puede ser un error o una advertencia.  
  
- Se representa mediante un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)