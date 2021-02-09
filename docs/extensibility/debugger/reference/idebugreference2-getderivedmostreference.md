---
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac8321bc571264d050f5f3559e840c3d169096d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909690"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtiene la referencia más derivada de una referencia. Reservado para un uso futuro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parámetros
`ppDerivedMost`\
enuncia Devuelve un objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa la propiedad más derivada.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="remarks"></a>Notas
 Por ejemplo, si esta propiedad describe un objeto que implementa `ClassRoot` pero que es realmente una instancia de `ClassDerived` que se deriva de `ClassRoot` , este método devuelve un objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa una referencia al `ClassDerived` objeto.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
