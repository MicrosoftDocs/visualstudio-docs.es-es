---
title: IDebugField::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa10836b91306a99629e80b6869880f018878c38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919354"
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

#### <a name="parameters"></a>Parámetros
 `pdwSize`

 [out] Devuelve el tamaño.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Todos los campos tienen un tipo y todos los tipos tienen un tamaño. Por ejemplo, un campo con un tipo de byte tiene un tamaño de 1 byte.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)