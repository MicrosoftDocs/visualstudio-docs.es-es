---
title: IDebugStackFrame3::InterceptCurrentException ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719480"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Llamado por el depurador en el marco de pila actual cuando desea interceptar la excepción actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parámetros
`dwFlags`\
[en] Especifica diferentes acciones. Actualmente, [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) solo `IEA_INTERCEPT` se admite el valor INTERCEPT_EXCEPTION_ACTION y debe especificarse.

`pqwCookie`\
[fuera] Valor único que identifica una excepción determinada.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

 Los siguientes son los retornos de error más comunes.

|Error|Descripción|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|La excepción actual no se puede interceptar.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|El marco de ejecución actual aún no se ha buscado para un controlador.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método no se admite para este marco.|

## <a name="remarks"></a>Observaciones
 Cuando se produce una excepción, el depurador obtiene el control del tiempo de ejecución en los puntos clave durante el proceso de control de excepciones. Durante estos momentos clave, el depurador puede preguntar al marco de pila actual si el marco desea interceptar la excepción. De este modo, una excepción interceptada es esencialmente un controlador de excepciones sobre la marcha para un marco de pila, incluso si ese marco de pila no tiene un controlador de excepciones (por ejemplo, un bloque try/catch en el código del programa).

 Cuando el depurador desea saber si se debe interceptar la excepción, llama a este método en el objeto de marco de pila actual. Este método es responsable de controlar todos los detalles de la excepción. Si el [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interfaz no `InterceptStackException` se implementa o el método devuelve cualquier error, a continuación, el depurador continúa procesando la excepción normalmente.

> [!NOTE]
> Las excepciones solo se pueden interceptar en código administrado, es decir, cuando el programa que se está depurando se ejecuta en tiempo de ejecución de .NET. Por supuesto, los implementadores de `InterceptStackException` lenguaje de terceros pueden implementar en sus propios motores de depuración si así lo desean.

 Una vez completada la interceptación, se señala un [IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

## <a name="see-also"></a>Vea también
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
