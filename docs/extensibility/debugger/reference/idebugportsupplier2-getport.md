---
description: Obtiene un puerto de un proveedor de puerto.
title: 'IDebugPortSupplier2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fa191b70e44684577845ab4a48c6c4f82844bce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145435"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Obtiene un puerto de un proveedor de puerto.

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
de Identificador único global (GUID) del puerto.

`ppPort`\
enuncia Devuelve un objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_PORTSUPPLIER_NO_PORT` si no existe ningún puerto con el identificador especificado.

## <a name="see-also"></a>Consulte también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
