---
title: IDebugPortSupplier2::RemovePort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db48cc82e16f071ec55493e98570c6969324bfda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918033"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Quita un puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

#### <a name="parameters"></a>Parámetros
 `pPort`

 [in] Un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa el puerto que se va a quitar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método quita el puerto de la lista interna del proveedor de puerto de puertos activos.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)