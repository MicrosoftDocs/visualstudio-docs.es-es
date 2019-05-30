---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 691df8f5a212f1d854d87076a215402c7ce0053c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310510"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtiene una descripción detallada de la excepción que se desencadena este evento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parámetros
`pExceptionInfo`\
[in, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura que se rellena con la descripción de la excepción.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios

 [C++ sólo] El llamador es responsable de liberar cualquier cadena de la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura, así como de liberar el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto de la estructura.

## <a name="see-also"></a>Vea también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)