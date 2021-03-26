---
description: Comprueba que un proveedor de puerto puede agregar nuevos puertos.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072213"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Comprueba que un proveedor de puerto puede agregar nuevos puertos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Valor devuelto
 Si se puede Agregar el puerto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` para indicar que no se pueden agregar puertos a este proveedor de puertos.

## <a name="remarks"></a>Observaciones
 Llame a este método antes de llamar al método [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , ya que el último método crea el puerto y lo agrega, lo que podría ser una operación que consume mucho tiempo.

## <a name="see-also"></a>Consulte también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
