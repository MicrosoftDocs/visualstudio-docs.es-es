---
title: Posición de documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc9d1e793405b2eb83fe4f72980a71e44d1acbd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926107"
---
# <a name="document-position"></a>Posición del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, un *documentar posición*:

- Proporciona una abstracción de una posición en un archivo de código fuente como sabe que el IDE. Para la mayoría de los lenguajes en la actualidad, una posición de documento puede considerarse como una posición en un archivo de origen.

- Describe una posición en un documento de origen a un motor de depuración.

- Se implementa mediante un [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto de documento](../../extensibility/debugger/document-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)