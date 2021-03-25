---
description: Determina si el campo representa un tipo cerrado.
title: 'IDebugExtendedField:: IsClosedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ba4c55b53ebb1f1e5ad2000f31efc8a37f81eef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077205"
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
 Si el campo es un tipo cerrado, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` .

## <a name="see-also"></a>Consulte también
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
