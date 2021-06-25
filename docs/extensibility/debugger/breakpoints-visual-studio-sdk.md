---
title: Puntos de interrupción (Visual Studio SDK) | Microsoft Docs
description: 'Obtenga información sobre los tres tipos de puntos de interrupción: pendiente, enlazado y error. En este artículo se enumeran las interfaces que se usan para implementar los tipos.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fce472faf95aa77f87ab02d78a3da640b6bd3bf
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901492"
---
# <a name="breakpoints-visual-studio-sdk"></a>Puntos de interrupción (Visual Studio SDK)
Hay tres tipos de puntos de interrupción: pendiente, enlazado y error.

 **Un punto de interrupción pendiente:**

- Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o varios contextos de código en uno o varios programas. Cada vez que un programa que se depura hace que se cargue código, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si se pueden enlazar.

   Un punto de interrupción pendiente nunca se enlaza al código, sino que recopila y se dice que contiene todos los puntos de interrupción enlazados que genera.

- Se representa mediante una [interfaz IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Un punto de interrupción enlazado:**

- Es una abstracción de un punto de interrupción asociado a o enlazado a un único contexto de código. Cada punto de interrupción enlazado se genera en respuesta a un punto de interrupción pendiente. Sin embargo, un punto de interrupción pendiente puede generar más de un punto de interrupción enlazado.

   Cuando se descarga el código, se puede desenlazchar y descartar un punto de interrupción enlazado.

- Se representa mediante una [interfaz IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Un punto de interrupción de error:**

- Es una abstracción para describir un error al intentar enlazar un punto de interrupción pendiente a un contexto de código. Un punto de interrupción de error describe un error en la ubicación o en la propia expresión de punto de interrupción. Para obtener más información, vea [Enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md).

   El error de punto de interrupción puede ser un error o una advertencia.

- Se representa mediante una [interfaz IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Consulta también
- [Programs](../../extensibility/debugger/programs.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
