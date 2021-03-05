---
description: Este método obtiene el tamaño de un campo, en bytes.
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
ms.openlocfilehash: 1c588914f93d732dc1b8e6ddc4edc41713e97fd1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151901"
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

## <a name="remarks"></a>Observaciones
 Todos los campos tienen un tipo y todos los tipos tienen un tamaño. Por ejemplo, un campo con un tipo de byte tiene un tamaño de 1 byte.

## <a name="see-also"></a>Consulte también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
