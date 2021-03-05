---
description: Lee instrucciones a partir de la posición actual en la secuencia de desensamblado.
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b963bddc9d1ee04a6955b1110d73934b30196b21
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160204"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lee instrucciones a partir de la posición actual en la secuencia de desensamblado.

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
de Número de instrucciones que se van a desensamblar. Este valor también es la longitud máxima de la `prgDisassembly` matriz.

`dwFields`\
de Combinación de marcas de la enumeración [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que indican los campos de que `prgDisassembly` se van a rellenar.

`pdwInstructionsRead`\
enuncia Devuelve el número de instrucciones que se desensamblan realmente.

`prgDisassembly`\
enuncia Una matriz de estructuras [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) que se rellena con el código desensamblado, una estructura por instrucción desensamblada. La longitud de esta matriz está dictada por el `dwInstructions` parámetro.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El número máximo de instrucciones disponibles en el ámbito actual se puede obtener llamando [al métodoful](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .

 La posición actual en la que se lee la siguiente instrucción de se puede cambiar llamando al método [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

 La `DSF_OPERANDS_SYMBOLS` marca se puede Agregar a la `DSF_OPERANDS` marca del `dwFields` parámetro para indicar que se deben usar nombres de símbolos al desensamblar instrucciones.

## <a name="see-also"></a>Consulte también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize (](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
