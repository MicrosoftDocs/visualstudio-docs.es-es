---
title: Posición del documento | Microsoft Docs
description: Obtenga información sobre cómo una posición de documento en Visual Studio depuración proporciona una abstracción de una posición en un archivo de código fuente, como conoce el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3ac3db62619c5d0eaa9e89e09d7d5def06ff1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898167"
---
# <a name="document-position"></a>Posición del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, una *posición de documento*:

- Proporciona una abstracción de una posición en un archivo de código fuente, como conoce el IDE. En la mayoría de los lenguajes actuales, una posición de documento se puede pensar como una posición en un archivo de código fuente.

- Describe una posición en un documento de origen para un motor de depuración.

- Se implementa mediante una [interfaz IDebugDocumentPosition2.](../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="see-also"></a>Consulta también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces del proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
