---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e15692a94e3f1c80d6bd6f12ecb0c2ce7271c8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876769"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Esta interfaz representa la posición inicial de una instrucción de código. Para la mayoría de las arquitecturas de tiempo de ejecución en la actualidad, un contexto de código puede considerarse como una dirección de flujo de ejecución de un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración implementa esta interfaz para relacionar la posición de una instrucción de código a una posición de documento.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Métodos de muchas interfaces devuelven esta interfaz, habitualmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). También se usa ampliamente con el [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfaz así como en la información de resolución de punto de interrupción.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos en el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaz, esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtiene el contexto del documento que corresponde al contexto de código activo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtiene la información de idioma para este contexto de código.|

## <a name="remarks"></a>Comentarios
 La diferencia clave entre una `IDebugCodeContext2` interfaz y un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaz es que un `IDebugCodeContext2` siempre están alineados a la instrucción. Esto significa que un `IDebugCodeContext2` siempre señala al principio de una instrucción, mientras que un `IDebugMemoryContext2` puede apuntar a cualquier byte de memoria de la arquitectura del tiempo de ejecución. `IDebugCodeContext2` se incrementa por instrucciones en lugar de por el tamaño de almacenamiento básico (normalmente bytes).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)