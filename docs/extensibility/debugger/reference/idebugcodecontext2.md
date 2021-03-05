---
description: Esta interfaz representa la posición inicial de una instrucción de código.
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 228b6e84ca2f85803c4a248b966698b822bb572f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164102"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Esta interfaz representa la posición inicial de una instrucción de código. Para la mayoría de las arquitecturas en tiempo de ejecución de hoy en día, un contexto de código puede considerarse una dirección en la secuencia de ejecución de un programa.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración implementa esta interfaz para relacionar la posición de una instrucción de código con una posición del documento.

## <a name="notes-for-callers"></a>Notas para llamadores
 Los métodos de muchas interfaces devuelven esta interfaz, normalmente [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). También se utiliza en gran medida con la interfaz [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) y en la información de resolución del punto de interrupción.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la interfaz [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtiene el contexto del documento que corresponde al contexto de código activo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtiene la información de lenguaje para este contexto de código.|

## <a name="remarks"></a>Observaciones
 La diferencia clave entre una `IDebugCodeContext2` interfaz y una interfaz [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) es que `IDebugCodeContext2` siempre se alinea con la instrucción. Esto significa que `IDebugCodeContext2` siempre apunta al principio de una instrucción, mientras que `IDebugMemoryContext2` puede apuntar a cualquier byte de memoria de la arquitectura en tiempo de ejecución. `IDebugCodeContext2` se incrementa mediante instrucciones en lugar de por el tamaño de almacenamiento básico (normalmente byte).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
