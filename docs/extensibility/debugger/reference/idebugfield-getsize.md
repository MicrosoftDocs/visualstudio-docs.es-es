---
title: 'IDebugField:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6330179f1bbfffcb1f590dfc09ae0c06385f12e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869861"
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
enuncia Devuelve el tamaño.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Todos los campos tienen un tipo y todos los tipos tienen un tamaño. Por ejemplo, un campo con un tipo de byte tiene un tamaño de 1 byte.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
