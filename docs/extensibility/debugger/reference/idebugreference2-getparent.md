---
description: Obtiene la referencia primaria de una referencia.
title: 'IDebugReference2:: GetParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9abb7c6f1d020244c930a4e884fcce5fdf23f5f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071418"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Obtiene la referencia primaria de una referencia. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

## <a name="parameters"></a>Parámetros
`ppParent`\
enuncia Devuelve un objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa el elemento primario de esta propiedad.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Consulte también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
