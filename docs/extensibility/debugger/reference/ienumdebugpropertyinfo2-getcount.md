---
title: IEnumDebugPropertyInfo2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::GetCount
helpviewer_keywords:
- IEnumDebugPropertyInfo2::GetCount
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1bdf42f52334b0b3bbc8e7044a4f1297831b24c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212051"
---
# <a name="ienumdebugpropertyinfo2getcount"></a>IEnumDebugPropertyInfo2::GetCount
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
[out] Devuelve el número de elementos de la enumeración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método no forma parte de la interfaz de enumeración COM habitual que especifica que solamente el `Next`, `Clone`, `Skip`, y `Reset` métodos deben implementarse.

## <a name="see-also"></a>Vea también
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)