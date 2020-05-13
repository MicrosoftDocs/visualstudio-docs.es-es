---
title: IDebugDisassemblyStream2::Leer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732096"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lee las instrucciones a partir de la posición actual en la secuencia de desmontaje.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parámetros
`dwInstructions`\
[en] El número de instrucciones que se deben desmontar. Este valor es también la `prgDisassembly` longitud máxima de la matriz.

`dwFields`\
[en] Una combinación de indicadores de la `prgDisassembly` [enumeración DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que indican qué campos se deben rellenar.

`pdwInstructionsRead`\
[fuera] Devuelve el número de instrucciones realmente desmontadas.

`prgDisassembly`\
[fuera] Matriz de estructuras [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) que se rellena con el código desensamblado, una estructura por instrucción desensamblada. La longitud de esta matriz `dwInstructions` viene determinada por el parámetro.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El número máximo de instrucciones que están disponibles en el ámbito actual se puede obtener mediante una llamada a la [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) método.

 La posición actual desde la que se lee la siguiente instrucción se puede cambiar llamando al método [Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

 La `DSF_OPERANDS_SYMBOLS` marca se puede `DSF_OPERANDS` agregar `dwFields` a la marca en el parámetro para indicar que los nombres de símbolo se deben utilizar al desmontar instrucciones.

## <a name="see-also"></a>Vea también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
