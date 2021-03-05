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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7402c2b5a367a3a0a681a9a17ef89872a7b3e96
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152980"
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
