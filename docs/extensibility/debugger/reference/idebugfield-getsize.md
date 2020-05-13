---
title: IDebugField::GetSize ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f19a914de2e74613e987753c8062215fd0d0403
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728810"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Este método obtiene el tamaño de un campo, en bytes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parámetros
`pdwSize`\
[fuera] Devuelve el tamaño.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Todos los campos tienen un tipo y todos los tipos tienen un tamaño. Por ejemplo, un campo con un tipo de byte tiene un tamaño de 1 byte.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
