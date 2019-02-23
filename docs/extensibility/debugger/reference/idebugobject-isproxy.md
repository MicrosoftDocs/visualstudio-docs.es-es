---
title: IDebugObject::IsProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 037245524446ded2ec250f1d4a04e21bf5924a61
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678428"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Determina si el objeto es un proxy transparente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

#### <a name="parameters"></a>Parámetros
 `pfIsProxy`

 [out] `TRUE` si el objeto es un proxy transparente; de lo contrario, `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se implementa mediante el motor de depuración de C++ de forma predeterminada.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)