---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5aefe3b348f36b32792ebce9600f846d5a9cffe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317830"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Este método obtiene las utilidades de equipo para un servidor.

> [!NOTE]
> Este método está obsoleto: no use ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método). Se conserva por motivos históricos.

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
[out] Devuelve un `IDebugMDMUtil2_V7` interfaz que representa la información de las utilidades de la máquina.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`, que indica que no se implementa el método.

## <a name="remarks"></a>Comentarios
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)