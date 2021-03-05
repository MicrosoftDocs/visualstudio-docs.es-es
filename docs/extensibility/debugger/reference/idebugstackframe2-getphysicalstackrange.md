---
description: Obtiene una representación dependiente del equipo del intervalo de direcciones físicas asociadas a un marco de pila.
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41664f0e59b0eba6ae8a98599c74bd91fe26cf2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145929"
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
enuncia Devuelve la dirección física más baja asociada a este marco de pila.

`paddrMax`\
enuncia Devuelve la dirección física más alta asociada a este marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El administrador de depuración de sesión (SDM) utiliza la información devuelta por este método para ordenar los marcos de pila.

 Se supone que la pila de llamadas aumenta de nivel, es decir, que los nuevos marcos de pila se agregan a direcciones de memoria cada vez más bajas. Una arquitectura en tiempo de ejecución debe proporcionar intervalos de pila físicos que coincidan con esta suposición.

## <a name="see-also"></a>Consulte también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
