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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840722"
---
# <a name="document-position"></a>Posición del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, una *posición de documento*:

- Proporciona una abstracción de una posición en un archivo de código fuente que se conoce en el IDE. Para la mayoría de los idiomas de hoy en día, una posición de documento puede considerarse como una posición en un archivo de código fuente.

- Describe una posición en un documento de origen a un motor de depuración.

- Se implementa mediante una interfaz [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Vea también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto del documento](../../extensibility/debugger/document-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
