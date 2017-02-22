---
title: "Contexto de documento | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración] y contextos"
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Contexto de documento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración, **un contexto del documento**:  
  
-   representa una posición en un archivo de código fuente.  Para los lenguajes donde el archivo de código fuente puede no estar presente, un contexto de documento identifica una posición en un documento generado normalmente el entorno en tiempo de ejecución.  Por ejemplo, un motor de script podría generar un documento de script.  Para obtener más información, vea [Posición del documento](../../extensibility/debugger/document-position.md).  
  
-   Describe una posición en un documento de origen que corresponde a un contexto del código.  El controlador de símbolos asigna un contexto del código en el contexto de la documentación, utilizando la información generada por un compilador o un intérprete.  
  
-   Se implementa mediante una interfaz de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
## Vea también  
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de proveedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)