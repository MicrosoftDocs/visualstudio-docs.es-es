---
title: IDebugPort2::GetPortSupplier ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 7a7b0615-df6b-4726-ab35-39dfa1ebed8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e0cc5f037631193b371078639ba3078be5b3fa4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725316"
---
# <a name="idebugport2getportsupplier"></a>IDebugPort2::GetPortSupplier
Obtiene el proveedor de puertos para este puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortSupplier( 
   IDebugPortSupplier2** ppSupplier
);
```

```csharp
int GetPortSupplier( 
   out IDebugPortSupplier2 ppSupplier
);
```

## <a name="parameters"></a>Parámetros
`ppSupplier`\
[fuera] Devuelve un [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) objeto representa el proveedor de puertopara un puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
