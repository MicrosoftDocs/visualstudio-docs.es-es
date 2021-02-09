---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3572390f6e047d0e06b645b6a364971fe4557ea8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904050"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Este método obtiene las utilidades del equipo para un servidor.

> [!NOTE]
> Este método está obsoleto: no use ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método). Se conserva por motivos históricos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parámetros
`ppUtil`\
enuncia Devuelve una `IDebugMDMUtil2_V7` interfaz que representa la información de las utilidades del equipo.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL` , que indica que no se ha implementado el método.

## <a name="remarks"></a>Notas
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
