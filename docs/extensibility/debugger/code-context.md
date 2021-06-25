---
title: Contexto de código | Microsoft Docs
description: Obtenga información sobre el contexto de código Visual Studio depuración, que describe una posición en el código que existe cuando un programa se ha detenido en un punto de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e3bd252990e52f4ecaede0cc5026067b28434bc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905727"
---
# <a name="code-context"></a>Contexto de código
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un **contexto de código**:

- Proporciona una abstracción de una posición en el código que el motor de depuración (DE) conoce. En la mayoría de las arquitecturas en tiempo de ejecución de hoy en día, un contexto de código se puede pensar como una dirección en el flujo de instrucciones de un programa. En el caso de los lenguajes no transaccionales, donde es posible que el código no se represente mediante instrucciones, un contexto de código puede representarse mediante otros medios.

- Describe la posición actual en el flujo de ejecución del programa que está depurando.

- Solo existe cuando un programa se ha detenido en un punto de interrupción.

- Tiene un contexto de documento asociado.

- Se implementa mediante una [interfaz IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Consulta también
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
