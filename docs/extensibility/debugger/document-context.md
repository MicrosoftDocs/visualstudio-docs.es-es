---
title: Contexto de documentos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a38d0ad28ad01b9e106cf06127b934dedfe5bba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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