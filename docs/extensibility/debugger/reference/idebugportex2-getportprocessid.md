---
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc1cb77d15c8825e0eb11243b40a08ff8287adbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311658"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Obtiene el identificador de proceso del puerto de sí mismo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parámetros
`pdwProcessId`\
[out] Devuelve el identificador de proceso físico del puerto de sí mismo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 En el tiempo de ejecución de Win32, por ejemplo, este método normalmente llama a la función de Win32 `GetCurrentProcessId` para obtener el identificador de proceso físicos.

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)