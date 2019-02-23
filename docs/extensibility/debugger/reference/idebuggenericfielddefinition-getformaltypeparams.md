---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22b02361b13a1fb639afc74fa7e0d8421a3ae19c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715783"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Recupera los parámetros de tipo dados el número de parámetros.

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

#### <a name="parameters"></a>Parámetros
 `cParams`

 [in] Número de parámetros.

 `ppParams`

 [out] Matriz de parámetros de tipo.

 `pcParams`

 [in, out] Número de parámetros de la `ppParams` matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Devuelve los parámetros de tipo de orden de izquierda a derecha. Por ejemplo, diccionario\<K, V > devuelve IDebugFormalGenericParameters {K, V}.

## <a name="see-also"></a>Vea también
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)