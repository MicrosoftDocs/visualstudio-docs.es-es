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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c53abba81b02aa6125d4fa25ce16db85579ce5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142666"
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
