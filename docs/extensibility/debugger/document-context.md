---
title: Contexto de documentos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="document-context"></a>Contexto del documento
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, un **contexto del documento**:  
  
-   Representa una posición en un archivo de código fuente. Para los idiomas en el archivo de origen no puede estar presente, un contexto de documento identifica una posición en un documento normalmente generado por el entorno de tiempo de ejecución. Por ejemplo, un motor de scripting puede generar un documento de script. Para obtener más información, consulte [posición del documento](../../extensibility/debugger/document-position.md).  
  
-   Describe una posición en un documento de origen que corresponde a un contexto de código. El controlador de símbolos, asigna un contexto de código al contexto de documentación, con la información generada por un compilador o intérprete.  
  
-   Se implementa mediante un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Contexto del código](../../extensibility/debugger/code-context.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)