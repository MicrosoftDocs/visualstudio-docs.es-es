---
title: IDebugReference2::GetParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f6f0aa96186557eba8549d899beed283558c1e7
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458720"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Obtiene la referencia primaria de una referencia. Reservado para un uso futuro.

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

 [out] Devuelve un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa el elemento primario de esta propiedad.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)