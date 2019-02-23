---
title: IDebugFunctionPosition2::GetFunctionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b98b1f2bcb8324544d88a9b002995ff472dec35d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716459"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Obtiene el nombre de la función a la que apunta esta posición.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetFunctionName( 
   BSTR* pbstrFunctionName
);
```

```csharp
int GetFunctionName(
   out string pbstrFunctionName
);
```

#### <a name="parameters"></a>Parámetros
 `pbstrFunctionName`

 [out] Devuelve el nombre de la función.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)