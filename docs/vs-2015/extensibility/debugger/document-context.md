---
title: Contexto del documento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200582"
---
# <a name="document-context"></a>Contexto de documento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración, un **contexto de documento**:  
  
- Representa una posición en un archivo de código fuente. En el caso de los idiomas en los que puede que el archivo de código fuente no esté presente, un contexto de documento identifica una posición en un documento que normalmente genera el entorno en tiempo de ejecución. Por ejemplo, un motor de scripting podría generar un documento a partir del script. Para obtener más información, vea [posición del documento](../../extensibility/debugger/document-position.md).  
  
- Describe una posición en un documento de origen que corresponde a un contexto de código. El controlador de símbolos asigna un contexto de código al contexto de documentación, usando la información generada por un compilador o intérprete.  
  
- Se implementa mediante una interfaz [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
