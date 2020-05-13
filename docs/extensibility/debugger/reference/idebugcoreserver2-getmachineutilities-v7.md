---
title: IDebugCoreServer2::GetMachineUtilities_V7 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733151"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Este método obtiene las utilidades de la máquina para un servidor.

> [!NOTE]
> Este método está obsoleto:[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] no `E_NOTIMPL` utilice (siempre devuelve si se llama a este método). Se conserva por razones históricas.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parámetros
`ppUtil`\
[fuera] Devuelve `IDebugMDMUtil2_V7` una interfaz que representa la información de utilidades de la máquina.

## <a name="return-value"></a>Valor devuelto
 Siempre `E_NOTIMPL`devuelve , lo que indica que el método no está implementado.

## <a name="remarks"></a>Observaciones
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]siempre `E_NOTIMPL` devuelve si se llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
