---
description: Este método determina si el proveedor del puerto puede conservar los puertos (escribiéndolo en el disco) entre las invocaciones del depurador.
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570409a114acbf19697b0eb3ef3e5496fdfde93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071979"
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

## <a name="remarks"></a>Observaciones
 Si el proveedor del puerto puede conservar los puertos, debe hacerlo cuando se destruya y volver a cargarlos cuando se vuelva a crear una instancia.

## <a name="see-also"></a>Consulte también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
