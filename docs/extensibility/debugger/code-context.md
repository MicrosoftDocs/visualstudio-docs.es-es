---
title: Contexto de código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11554be1411e63c97c8afde7cc3a819486e862ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351322"
---
# <a name="code-context"></a>Contexto de código
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, un **contexto del código**:

- Proporciona una abstracción de una posición en el código tal y como se sabe que el motor de depuración (DE). Para la mayoría de las arquitecturas de tiempo de ejecución en la actualidad, un contexto de código puede considerarse como una dirección en la secuencia de instrucciones de un programa. Para los idiomas no tradicionales, donde no se puede representar código por instrucciones, se puede representar un contexto de código por otros medios.

- Describe la posición actual en la secuencia de ejecución del programa que está depurando.

- Existe solo cuando se ha detenido un programa en un punto de interrupción.

- Tiene un contexto de documento asociado.

- Se implementa mediante un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Contexto de documento](../../extensibility/debugger/document-context.md)
- [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)