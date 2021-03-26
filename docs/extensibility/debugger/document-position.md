---
title: Posición del documento | Microsoft Docs
description: Obtenga información sobre cómo una posición de documento en la depuración de Visual Studio proporciona una abstracción de una posición en un archivo de código fuente que se conoce en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097258"
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
