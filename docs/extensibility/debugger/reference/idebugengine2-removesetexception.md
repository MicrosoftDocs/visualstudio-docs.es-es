---
description: Quita la excepción especificada para que el motor de depuración ya no la administre.
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 588037ef9dcf495f8fbbb210acc3154c31558a32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153954"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Quita la excepción especificada para que el motor de depuración ya no la administre.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parámetros
`pException`\
de Estructura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) que describe la excepción que se va a quitar.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La excepción que se va a quitar se debe haber establecido previamente mediante una llamada anterior al método [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Para quitar todas las excepciones set a la vez, llame al método [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
