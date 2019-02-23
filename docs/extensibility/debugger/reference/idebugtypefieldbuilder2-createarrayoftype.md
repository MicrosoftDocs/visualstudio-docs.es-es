---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ad86b7bbd68a6fc449efe650a134ab92458d12e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693742"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Crea una matriz del tipo especificado y el tamaño.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateArrayOfType (
   IDebugField*  pTypeField,
   DWORD         rank,
   IDebugField** pArrayOfTypeField
);
```

```csharp
int CreateArrayOfType (
   IDebugField     pTypeField,
   uint            rank,
   out IDebugField pArrayOfTypeField
);
```

#### <a name="parameters"></a>Parámetros
 `pTypeField`

 [in] Tipo de elementos que se va a contener la matriz.

 `rank`

 [in] Número de elementos de la matriz.

 `pArrayOfTypeField`

 [out] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan la nueva matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)