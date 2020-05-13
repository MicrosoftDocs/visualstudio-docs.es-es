---
title: IDebugCodeContext2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734214"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Esta interfaz representa la posición inicial de una instrucción de código. Para la mayoría de las arquitecturas en tiempo de ejecución actuales, un contexto de código se puede considerar como una dirección en la secuencia de ejecución de un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración implementa esta interfaz para relacionar la posición de una instrucción de código con una posición de documento.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Los métodos de muchas interfaces devuelven esta interfaz, normalmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). También se utiliza ampliamente con la [interfaz IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) así como en la información de resolución de punto de interrupción.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la interfaz [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtiene el contexto del documento que corresponde al contexto de código activo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtiene la información de idioma para este contexto de código.|

## <a name="remarks"></a>Observaciones
 La diferencia clave `IDebugCodeContext2` entre una interfaz y una `IDebugCodeContext2` [interfaz IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) es que siempre está alineado con instrucciones. Esto significa `IDebugCodeContext2` que un siempre apunta al principio de `IDebugMemoryContext2` una instrucción, mientras que un puede apuntar a cualquier byte de memoria en la arquitectura en tiempo de ejecución. `IDebugCodeContext2`se incrementa por instrucciones en lugar de por el tamaño de almacenamiento básico (normalmente byte).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
