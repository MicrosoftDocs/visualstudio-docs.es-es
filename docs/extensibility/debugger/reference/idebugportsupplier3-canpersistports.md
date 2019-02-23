---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad31d015048d8e0732c32652141b7be060628663
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722634"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina si el proveedor del puerto puede conservar los puertos (escribiéndolas en el disco) entre las distintas invocaciones del depurador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

#### <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 `S_OK` Si se pueden conservar los puertos, o `S_FALSE` para indicar que no se pueden conservar los puertos.

## <a name="remarks"></a>Comentarios
 Si el proveedor del puerto puede persistir los puertos, debe hacerlo cuando se destruye y, a continuación, volver a cargarlos cuando se crean instancias de una vez más.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)