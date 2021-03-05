---
description: Obtiene una descripción detallada de la excepción que desencadenó este evento.
title: 'IDebugExceptionEvent2:: GetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6505cd2309323d7fe91f2c807af33555c3575fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152902"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtiene una descripción detallada de la excepción que desencadenó este evento.

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
[in, out] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura que se rellena con la descripción de la excepción.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

 [Solo C++] El autor de la llamada es responsable de liberar cualquier cadena de la estructura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) y de liberar el objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) de la estructura.

## <a name="see-also"></a>Consulte también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
