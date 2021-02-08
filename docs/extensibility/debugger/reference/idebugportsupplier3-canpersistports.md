---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2914d56f2d74629a30bc63bad281bb0cdcdc0de8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840345"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina si el proveedor del puerto puede conservar los puertos (escribiéndolo en el disco) entre las invocaciones del depurador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 `S_OK` Si los puertos pueden persistir o `S_FALSE` para indicar que no se pueden conservar los puertos.

## <a name="remarks"></a>Notas
 Si el proveedor del puerto puede conservar los puertos, debe hacerlo cuando se destruya y volver a cargarlos cuando se vuelva a crear una instancia.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
