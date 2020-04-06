---
title: Puntos de interrupción (SDK de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739189"
---
# <a name="breakpoints-visual-studio-sdk"></a>Puntos de interrupción (Visual Studio SDK)
Hay tres tipos de puntos de interrupción: pendiente, enlazado y error.

 **Un punto de interrupción pendiente:**

- Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o varios contextos de código en uno o varios programas. Cada vez que un programa que se está depurando hace que el código se cargue, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si se pueden enlazar.

   Un punto de interrupción pendiente nunca se enlaza al código, sino que se recopila y se dice que contiene todos los puntos de interrupción enlazados que genera.

- Se representa mediante un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.

  **Un punto de interrupción enlazado:**

- Es una abstracción para un punto de interrupción asociado o enlazado a un único contexto de código. Cada punto de interrupción enlazado se genera en respuesta a un punto de interrupción pendiente. Sin embargo, un punto de interrupción pendiente puede generar más de un punto de interrupción enlazado.

   Cuando se descarga código, un punto de interrupción enlazado se puede desenlazar y descartar.

- Se representa mediante un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.

  **Un punto de interrupción de error:**

- Es una abstracción para describir un error al intentar enlazar un punto de interrupción pendiente a un contexto de código. Un punto de interrupción de error describe un error en la ubicación o en la propia expresión de punto de interrupción. Para obtener más información, vea Puntos de [interrupción](../../extensibility/debugger/binding-breakpoints.md)de enlace .

   El error de punto de interrupción puede ser un error o una advertencia.

- Se representa mediante un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Programs](../../extensibility/debugger/programs.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Contexto del código](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
