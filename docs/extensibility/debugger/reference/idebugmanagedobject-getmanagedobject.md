---
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18cb56b083386c3ac8358a101c1d52fb14cb39ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890245"
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

## <a name="remarks"></a>Notas
 La interfaz devuelta por este método se puede consultar para cualquier interfaz implementada por la clase administrada, lo que permite llamar a sus métodos.

## <a name="see-also"></a>Vea también
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
