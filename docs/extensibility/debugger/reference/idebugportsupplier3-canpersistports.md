---
title: IDebugPortSupplier3::CanPersistPorts ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724463"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina si el proveedor de puertos puede conservar los puertos (escribiéndolos en el disco) entre las invocaciones del depurador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 `S_OK`si los puertos se `S_FALSE` pueden conservar, o para indicar que los puertos no se pueden conservar.

## <a name="remarks"></a>Observaciones
 Si el proveedor de puertos puede conservar los puertos, debe hacerlo cuando se destruye y, a continuación, volver a cargarlos cuando se crea una instancia una vez más.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
