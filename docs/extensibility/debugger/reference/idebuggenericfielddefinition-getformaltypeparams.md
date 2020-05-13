---
title: IDebugGenericFieldDefinition::GetFormalTypeParams ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4926d94e4ba032f3ff10ca8fdf7027ac6f6e751c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728246"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Recupera los parámetros de tipo dado el número de parámetros.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetFormalTypeParams(
   ULONG32                   cParams,
   IDebugGenericParamField** ppParams,
   ULONG32*                  pcParams
);
```

```csharp
int GetFormalTypeParams(
   uint                          cParams,
   out IDebugGenericParamField[] ppParams,
   ref uint                      pcParams
);
```

## <a name="parameters"></a>Parámetros
`cParams`\
[en] Número de parámetros.

`ppParams`\
[fuera] Matriz de parámetros de tipo.

`pcParams`\
[adentro, fuera] Número de parámetros de la `ppParams` matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Devuelve los parámetros de tipo en orden de izquierda a derecha. Por ejemplo,\<el diccionario K,V> devuelve IDebugFormalGenericParameters .

## <a name="see-also"></a>Vea también
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
