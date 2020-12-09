---
title: Posición del documento | Microsoft Docs
description: Obtenga información sobre cómo una posición de documento en la depuración de Visual Studio proporciona una abstracción de una posición en un archivo de código fuente que se conoce en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915328"
---
# <a name="document-position"></a>Posición del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, una *posición de documento*:

- Proporciona una abstracción de una posición en un archivo de código fuente que se conoce en el IDE. Para la mayoría de los idiomas de hoy en día, una posición de documento puede considerarse como una posición en un archivo de código fuente.

- Describe una posición en un documento de origen a un motor de depuración.

- Se implementa mediante una interfaz [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Consulte también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
