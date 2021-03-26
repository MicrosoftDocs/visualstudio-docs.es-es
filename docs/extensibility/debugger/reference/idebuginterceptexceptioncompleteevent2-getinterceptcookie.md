---
description: Se llama cuando se ha completado el procesamiento de una excepción interceptada.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c0cdf514f606287386c68713371d112cb97e79
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091921"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Se llama cuando se ha completado el procesamiento de una excepción interceptada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parámetros
`pqwCookie`\
enuncia Valor único que está asociado a la excepción que se ha interceptado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 Después de que el método [interceptcurrentexception (](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) haya completado el control de una excepción interceptada, envía el evento [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) . El controlador puede utilizar el `GetInterceptCookie` método para recuperar el valor único asociado a la excepción (el mismo valor pasado al `InterceptCurrentException` método).

## <a name="see-also"></a>Consulte también
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
