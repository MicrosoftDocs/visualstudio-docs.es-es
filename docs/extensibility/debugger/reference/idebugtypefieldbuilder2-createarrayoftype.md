---
title: IDebugTypeFieldBuilder2::CreateArrayOfType ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d7a229ea92b57252a9f01976e7b5c80348bd314
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718316"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Crea una matriz del tipo y tamaño especificados.

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

## <a name="parameters"></a>Parámetros
`pTypeField`\
[en] Tipo de elementos que la matriz contendrá.

`rank`\
[en] Número de elementos de la matriz.

`pArrayOfTypeField`\
[fuera] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan la nueva matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)
