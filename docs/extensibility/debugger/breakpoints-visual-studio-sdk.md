---
title: Puntos de interrupción (SDK de Visual Studio) | Microsoft Docs
description: 'Obtenga información sobre los tres tipos de puntos de interrupción: pendiente, enlazado y error. En este artículo se enumeran las interfaces utilizadas para implementar los tipos.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa9f244ec60e336e9a7596ff839842211d516b7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930816"
---
# <a name="breakpoints-visual-studio-sdk"></a>Puntos de interrupción (Visual Studio SDK)
Hay tres tipos de puntos de interrupción: pendiente, enlazado y error.

 **Un punto de interrupción pendiente:**

- Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o más contextos de código en uno o varios programas. Cada vez que se depura un programa que hace que se cargue el código, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si se pueden enlazar.

   Un punto de interrupción pendiente nunca se enlaza al código, sino que recopila y se dice que contiene todos los puntos de interrupción enlazados que genera.

- Se representa mediante una interfaz [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Un punto de interrupción enlazado:**

- Es una abstracción para un punto de interrupción asociado con o enlazado a un contexto de código único. Cada punto de interrupción enlazado se genera como respuesta a un punto de interrupción pendiente. Sin embargo, un punto de interrupción pendiente puede generar más de un punto de interrupción enlazado.

   Cuando se descarga el código, se puede Desenlazar y descartar un punto de interrupción enlazado.

- Se representa mediante una interfaz [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Un punto de interrupción de error:**

- Es una abstracción para describir un error al intentar enlazar un punto de interrupción pendiente a un contexto de código. Un punto de interrupción de error describe un error en la ubicación o en la propia expresión de punto de interrupción. Para obtener más información, vea [enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md).

   El error de punto de interrupción puede ser un error o una advertencia.

- Se representa mediante una interfaz [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Vea también
- [Programs](../../extensibility/debugger/programs.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
