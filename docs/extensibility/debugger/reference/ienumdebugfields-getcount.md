---
title: 'IEnumDebugFields:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5725d16577b9d22d280b17cc572b7335cd2331ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896919"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Este método devuelve el número de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parámetros
`pcelt`\
enuncia Devuelve el número de elementos de la enumeración.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Este método no forma parte de la interfaz de enumeración COM personalizada, que especifica que solo se deben implementar los siguientes, clonar, omitir y restablecer.

## <a name="see-also"></a>Vea también
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
