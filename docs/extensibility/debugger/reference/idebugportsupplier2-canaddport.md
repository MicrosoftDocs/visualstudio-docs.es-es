---
title: IDebugPortSupplier2::CanAddPort ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724750"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Comprueba que un proveedor de puertos puede agregar nuevos puertos.

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
 Si se puede agregar `S_OK`el puerto, devuelve ; de lo `S_FALSE` contrario, las devoluciones para indicar que no se pueden agregar puertos a este proveedor de puertos.

## <a name="remarks"></a>Observaciones
 Llame a este método antes de llamar a la [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) método ya que este último método crea el puerto, así como agregarlo, que podría ser una operación que consume mucho tiempo.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
