---
title: Contexto de documento | Microsoft Docs
description: Obtenga información sobre el contexto del documento Visual Studio depuración, que representa una posición en un archivo de código fuente o una posición en un documento de origen para un contexto de código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898193"
---
# <a name="document-context"></a>Contexto del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un *contexto de documento*:

- Representa una posición en un archivo de código fuente. Para los idiomas en los que es posible que el archivo de origen no esté presente, un contexto de documento identifica una posición en un documento generado normalmente por el entorno en tiempo de ejecución. Por ejemplo, un motor de scripting podría generar un documento a partir de script. Para obtener más información, vea [Posición del documento.](../../extensibility/debugger/document-position.md)

- Describe una posición en un documento de origen que corresponde a un contexto de código. El controlador de símbolos asigna un contexto de código al contexto de documentación, utilizando la información generada por un compilador o intérprete.

- Se implementa mediante una [interfaz IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Consulta también
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces del proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
