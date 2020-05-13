---
title: IDebugGenericFieldInstance::TypeArgumentCount ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0272e86f5c1bbbd840ee222b2048440338302d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728153"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Devuelve el número de argumentos de parámetro de tipo para esta instancia.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parámetros
`pcArgs`\
[adentro, fuera] Número de argumentos de parámetro de tipo para esta instancia.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Por ejemplo,\<si List int>, este método\<devuelve 1 y, si List int,float2> este método devuelve 2. Este método devuelve 0 si no hay ningún argumento de tipo.

## <a name="see-also"></a>Vea también
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
