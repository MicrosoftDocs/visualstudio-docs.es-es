---
description: Obtiene los atributos para este evento de depuración.
title: 'IDebugEvent2:: GetAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b41e3f50b73c16c9acb28a809b8c33b535370c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065858"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtiene los atributos para este evento de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Parámetros
`pdwAttrib`\
enuncia Combinación de marcas de la enumeración [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) es común a todos los eventos. Este método describe el tipo de evento; por ejemplo, es el evento sincrónico o asincrónico y es un evento de detención.

## <a name="see-also"></a>Consulte también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
