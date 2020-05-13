---
title: IDebugPortSupplier2::GetPort ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be3f53c12b5562377cd79267d6e216a1435859a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724656"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Obtiene un puerto de un proveedor de puertos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parámetros
`guidPort`\
[en] Identificador único global (GUID) del puerto.

`ppPort`\
[fuera] Devuelve un [objeto IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_PORTSUPPLIER_NO_PORT` si no existe ningún puerto con el identificador especificado.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
