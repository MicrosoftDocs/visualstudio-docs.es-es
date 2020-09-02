---
title: 'IEnumDebugErrorBreakpoints2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
ms.assetid: 56f7bb70-d55b-471c-8c65-09a9e7f4938e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 867b0e699ac1e4874a6ac3db12eb52daa27758d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716984"
---
# <a name="ienumdebugerrorbreakpoints2getcount"></a>IEnumDebugErrorBreakpoints2::GetCount
Devuelve el número de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCount(
   ULONG* pcelt
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

## <a name="remarks"></a>Observaciones
 Este método no forma parte de la interfaz de enumeración com personalizada, que especifica que `Next` solo `Clone` `Skip` `Reset` se deben implementar los métodos,, y.

## <a name="see-also"></a>Vea también
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
