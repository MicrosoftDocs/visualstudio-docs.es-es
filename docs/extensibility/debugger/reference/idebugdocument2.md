---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "Interfaz IDebugDocument2"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un documento de origen.  
  
## Sintaxis  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## Notas para los implementadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] normalmente implementa esta interfaz.  Un motor de depuración \(DE\) puede implementar esta interfaz cuando necesita proporcionar el código fuente y el origen no existe en el disco.  En casos como éste, el OF también debería implementar las interfaces de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) y de [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , así como algunos métodos adicionales en las interfaces de [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) y de [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .  
  
## Notas para los llamadores  
 Los métodos de `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, e interfaces de `IDebugActivateDocumentEvent2` devuelven esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugDocument2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtiene el nombre del documento en una de varias formas.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtiene el identificador de clase del documento.|  
  
## Comentarios  
 Se implementa esta interfaz cuando el OF supplies el código fuente.  Por ejemplo, al depurar el script en una página HTML, el OF supplies el código fuente porque el origen se descarga o se genera dinámicamente y no existe como archivo de disco.  Al depurar lenguajes tradicionales, como C\+\+, esta interfaz no necesita implementar.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)