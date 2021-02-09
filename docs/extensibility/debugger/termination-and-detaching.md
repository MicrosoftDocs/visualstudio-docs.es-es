---
title: Terminación y desasociación | Microsoft Docs
description: La terminación normal significa que un programa que se está depurando se ejecuta hasta su finalización sin puntos de interrupción, excepciones, errores en tiempo de ejecución o bucles infinitos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895900"
---
# <a name="termination-and-detaching"></a>Terminación y desasociación
En la siguiente sección se describe la terminación normal.

## <a name="discussion"></a>Debate
 Después de que la interfaz [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continúe, si no hay puntos de interrupción, excepciones, errores en tiempo de ejecución o bucles infinitos en la aplicación que se va a depurar, el programa que se está depurando se ejecuta hasta su finalización. Este proceso es una finalización normal.

 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la terminación normal. La terminación normal requiere la ejecución del método [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Vea también
- [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
