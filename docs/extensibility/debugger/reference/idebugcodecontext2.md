---
title: IDebugCodeContext2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b46ec36a93ac91647a3f17aac28187519ca2447
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103882"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Esta interfaz representa la posición inicial de una instrucción de código. Para la mayoría de tiempo de ejecución de arquitecturas en la actualidad, un contexto de código puede considerarse como una dirección de flujo de ejecución de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración implementa esta interfaz para relacionar la posición de una instrucción de código a una posición del documento.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Métodos en muchas interfaces devuelven esta interfaz, normalmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). También se utiliza mucho con el [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfaz así como en la información de resolución de punto de interrupción.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtiene el contexto del documento que corresponde al contexto de código activo.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtiene la información de idioma para este contexto de código.|  
  
## <a name="remarks"></a>Comentarios  
 La diferencia clave entre una `IDebugCodeContext2` interfaz y un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaz es que un `IDebugCodeContext2` siempre están alineados a la instrucción. Esto significa que un `IDebugCodeContext2` siempre señala al principio de una instrucción, mientras que un `IDebugMemoryContext2` pueden señalar a los bytes de memoria de la arquitectura del tiempo de ejecución. `IDebugCodeContext2` se incrementa por instrucciones en lugar de por el tamaño de almacenamiento de información básica (normalmente bytes).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)