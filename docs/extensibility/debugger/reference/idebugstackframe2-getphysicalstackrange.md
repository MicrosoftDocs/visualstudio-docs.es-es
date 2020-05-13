---
title: IDebugStackFrame2::GetPhysicalStackRange ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719671"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtiene una representación dependiente del equipo del intervalo de direcciones físicas asociadas a un marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parámetros
`paddrMin`\
[fuera] Devuelve la dirección física más baja asociada a este marco de pila.

`paddrMax`\
[fuera] Devuelve la dirección física más alta asociada a este marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El administrador de depuración de sesión (SDM) utiliza la información devuelta por este método para ordenar los marcos de pila.

 Se supone que la pila de llamadas crece hacia abajo, es decir, que las nuevas tramas de pila se agregan en direcciones de memoria cada vez más bajas. Una arquitectura en tiempo de ejecución debe proporcionar intervalos de pila físicos que coincidan con esta suposición.

## <a name="see-also"></a>Vea también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
