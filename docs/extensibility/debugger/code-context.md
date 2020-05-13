---
title: Contexto de código ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739156"
---
# <a name="code-context"></a>Contexto del código
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un contexto de **código:**

- Proporciona una abstracción de una posición en el código como se conoce al motor de depuración (DE). Para la mayoría de las arquitecturas en tiempo de ejecución actuales, un contexto de código se puede considerar como una dirección en la secuencia de instrucciones de un programa. Para los lenguajes no tradicionales, donde el código puede no estar representado por instrucciones, un contexto de código puede estar representado por otros medios.

- Describe la posición actual en la secuencia de ejecución del programa que está depurando.

- Sólo existe cuando un programa se ha detenido en un punto de interrupción.

- Tiene un contexto de documento asociado.

- Se implementa mediante un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
