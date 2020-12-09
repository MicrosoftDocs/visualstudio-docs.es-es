---
title: Llamar a eventos del depurador | Microsoft Docs
description: Los eventos de las sesiones de depuración se producen en un orden específico. En este artículo se muestra el orden de llamada de los eventos que se producen en una sesión de depuración típica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 832b42e62731a087048b4aa50e19b74c408343c5
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914393"
---
# <a name="call-debugger-events"></a>Llamar a eventos del depurador
Los eventos de las sesiones de depuración se producen en un orden específico.

## <a name="discussion"></a>Discusión
 Para entender el patrón de llamadas entre el motor de depuración (DE) y el administrador de depuración de sesión (SDM), lo siguiente representa el orden de llamada de los eventos que se producen en una sesión de depuración típica:

1. [Adjuntar y desasociar a un programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Iniciar el depurador](../../extensibility/debugger/launching-the-debugger.md)

3. [Finalización de un programa](../../extensibility/debugger/terminating-a-program.md)

4. [Crear un punto de interrupción](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Cuando un punto de interrupción se enlaza o se convierte en independiente](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Errores de punto de interrupción](../../extensibility/debugger/breakpoint-errors.md)

7. [Golpear un punto de interrupción](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Eliminar un punto de interrupción](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Entrar en modo de interrupción](../../extensibility/debugger/entering-break-mode.md)

10. [Ejecución paso a paso en modo de interrupción](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Control de excepciones](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Consulte también
- [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
