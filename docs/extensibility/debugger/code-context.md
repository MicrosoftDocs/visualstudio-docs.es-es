---
title: Contexto de código | Microsoft Docs
description: Obtenga información sobre el contexto de código en la depuración de Visual Studio, que describe una posición en el código que existe cuando un programa se detiene en un punto de interrupción.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 60eabaca8d39d40649e20e022b25ce1b02bd8faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914314"
---
# <a name="code-context"></a>Contexto de código
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un **contexto de código**:

- Proporciona una abstracción de una posición en el código tal y como lo conoce el motor DE depuración (DE). Para la mayoría de las arquitecturas en tiempo de ejecución de hoy en día, un contexto de código puede considerarse una dirección en el flujo de instrucciones de un programa. En el caso de los lenguajes no tradicionales, donde el código no se puede representar mediante instrucciones, un contexto de código puede representarse por otros medios.

- Describe la posición actual en la secuencia de ejecución del programa que se está depurando.

- Solo existe cuando un programa se ha detenido en un punto de interrupción.

- Tiene un contexto de documento asociado.

- Se implementa mediante una interfaz [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Consulte también
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
