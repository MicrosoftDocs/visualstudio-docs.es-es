---
description: Devuelve un objeto de contexto de código correspondiente a un identificador de ubicación de código especificado.
title: 'IDebugDisassemblyStream2:: GetCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c532c68435d1eaabdb03f8acae571ac4b71a5a7b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067080"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Devuelve un objeto de contexto de código correspondiente a un identificador de ubicación de código especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parámetros
`uCodeLocationId`\
de Especifica el identificador de ubicación del código. Vea la sección Comentarios del método [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obtener una descripción de un identificador de ubicación de código.

`ppCodeContext`\
enuncia Devuelve un objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa el contexto de código asociado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El identificador de ubicación del código se puede devolver desde una llamada al método [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) y puede aparecer en la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

 Para convertir un contexto de código en un identificador de ubicación de código, llame al método [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

## <a name="see-also"></a>Consulte también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
