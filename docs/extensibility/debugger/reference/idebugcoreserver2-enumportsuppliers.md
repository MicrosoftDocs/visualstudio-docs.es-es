---
title: 'IDebugCoreServer2:: EnumPortSuppliers | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPortSuppliers
helpviewer_keywords:
- IDebugCoreServer2::EnumPortSuppliers
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df295625a7e21dbfe13150e05e4b0ecbfa08f694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904182"
---
# <a name="idebugcoreserver2enumportsuppliers"></a>IDebugCoreServer2::EnumPortSuppliers
Recupera una lista de todos los proveedores de puertos disponibles.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumPortSuppliers(
   IEnumDebugPortSuppliers2** ppEnum
);
```

```csharp
int EnumPortSuppliers(
   out IEnumDebugPortSuppliers2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) que contiene una lista de todos los proveedores de puertos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
