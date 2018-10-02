---
title: Contexto de documento | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a9e92976af5e098dca0d1a4bb81c777eb38a9f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577511"
---
# <a name="document-context"></a>Contexto de documento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [contexto de documento](https://docs.microsoft.com/visualstudio/extensibility/debugger/document-context).  
  
En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración, un **contexto de documento**:  
  
-   Representa una posición en un archivo de origen. Para los idiomas donde el archivo de origen no puede estar presente, un contexto de documento identifica una posición en un documento normalmente generado por el entorno de tiempo de ejecución. Por ejemplo, un motor de scripting podría generar un documento de script. Para obtener más información, consulte [posición del documento](../../extensibility/debugger/document-position.md).  
  
-   Describe una posición en un documento de origen que corresponde a un contexto de código. El controlador de símbolos asigna un contexto de código al contexto de la documentación, con información generada por un compilador o intérprete.  
  
-   Se implementa mediante un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)

