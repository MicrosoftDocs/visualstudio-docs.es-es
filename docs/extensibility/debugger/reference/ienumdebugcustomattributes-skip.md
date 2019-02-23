---
title: IEnumDebugCustomAttributes::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 372a32d83f0cebf69fd5e7795e083a272bbeb588
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679832"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Omite un número especificado de atributos personalizados en una secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Skip ( 
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

#### <a name="parameters"></a>Parámetros
 `celt`

 [in] Número de elementos que se van a omitir.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el extremo y `S_FALSE` se devuelve.

## <a name="see-also"></a>Vea también
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)