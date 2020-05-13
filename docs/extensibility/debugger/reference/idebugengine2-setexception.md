---
title: IDebugEngine2::SetException ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7398db3c15c58821e05eff839a1022276401d569
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730935"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Especifica cómo el motor de depuración (DE) debe controlar una excepción determinada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parámetros
`pException`\
[en] Una [estructura EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) que describe la excepción y cómo depurarla.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un DE podría ser instruido para detener el programa generando una excepción en la primera oportunidad, segunda oportunidad, o no en absoluto.

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
