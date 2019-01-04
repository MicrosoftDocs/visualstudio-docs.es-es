---
title: IDebugDocumentContext2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dca62a511cd247f3344e319a7c3b4946b848103f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909704"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Esta interfaz representa una posición en un documento de archivo de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad para depurar el código fuente nivel. Además de una posición en el código fuente, esta interfaz proporciona métodos para comparar los contextos y navegar por un documento de código fuente.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Métodos de varias interfaces, normalmente la [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) y [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfaces, devolver esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugDocumentContext2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Obtiene el documento que contiene el contexto de este documento.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Obtiene el nombre del documento que contiene este contexto de documento que se puede mostrar.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera una lista de todos los contextos de código asociado con este contexto de documento.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Obtiene el idioma asociado a este contexto de documento.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de la instrucción de archivo de este contexto de documento.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Obtiene el intervalo de origen de archivo de este contexto de documento.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Compara este contexto de documento a una matriz de contextos de documento determinada.|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Mueva el contexto del documento mediante un número determinado de las instrucciones o líneas.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)