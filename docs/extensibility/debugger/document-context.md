---
title: Contexto del documento | Microsoft Docs
description: Obtenga información sobre el contexto de documento en la depuración de Visual Studio, que representa una posición en un archivo de código fuente o una posición en un documento de origen para un contexto de código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d19830346ea09731dde608e019109f61011cd60
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915536"
---
# <a name="document-context"></a>Contexto del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un *contexto de documento*:

- Representa una posición en un archivo de código fuente. En el caso de los idiomas en los que puede que el archivo de código fuente no esté presente, un contexto de documento identifica una posición en un documento que normalmente genera el entorno en tiempo de ejecución. Por ejemplo, un motor de scripting podría generar un documento a partir del script. Para obtener más información, vea [posición del documento](../../extensibility/debugger/document-position.md).

- Describe una posición en un documento de origen que corresponde a un contexto de código. El controlador de símbolos asigna un contexto de código al contexto de documentación, usando la información generada por un compilador o intérprete.

- Se implementa mediante una interfaz [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Consulte también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
