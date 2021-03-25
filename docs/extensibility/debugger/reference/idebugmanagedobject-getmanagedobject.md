---
description: Devuelve una interfaz que representa el objeto administrado.
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1aea4f233160f9bdcc5c18c1dda16b4e3f361540
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076945"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Devuelve una interfaz que representa el objeto administrado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parámetros
`ppManagedObject`\
enuncia Devuelve una interfaz que representa el objeto administrado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La interfaz devuelta por este método se puede consultar para cualquier interfaz implementada por la clase administrada, lo que permite llamar a sus métodos.

## <a name="see-also"></a>Consulte también
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
