---
title: IDebugExtendedField::IsClosedType ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4524d7c899480518e669f1f77a4756a83e0cf52f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729055"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Determina si el campo representa un tipo cerrado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Valor devuelto
 Si el campo es un `S_OK`tipo cerrado, devuelve ; de lo `S_FALSE`contrario, devuelve .

## <a name="see-also"></a>Vea también
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
