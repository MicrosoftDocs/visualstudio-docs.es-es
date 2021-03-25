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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b763291fccd39d46b32347d89df1a11e1b3d09f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095412"
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
