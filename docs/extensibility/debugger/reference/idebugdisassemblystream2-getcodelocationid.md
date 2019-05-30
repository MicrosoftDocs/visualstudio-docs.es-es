---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58e3b12ecbc75b7d07d60ac399412dc5b0deb73b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351693"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Devuelve un identificador de ubicación de código para un contexto de código determinado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parámetros
`pCodeContext`\
[in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto va a convertir en un identificador.

`puCodeLocationId` [out] Devuelve el identificador de ubicación del código. Vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_CODE_CONTEXT_OUT_OF_SCOPE` si el contexto de código es válido, pero fuera del ámbito.

## <a name="remarks"></a>Comentarios
 El identificador de ubicación del código es específico para el motor de depuración (DE) que admiten el desensamblado. Este identificador de ubicación se utiliza internamente por la DE para realizar el seguimiento de las posiciones en el código y suele ser una dirección o el desplazamiento de algún tipo. El único requisito es que si el contexto del código de una ubicación es menor que el contexto del código de otra ubicación, el identificador de ubicación de código correspondiente del primer contexto de código también debe ser menor que el identificador de ubicación del código del segundo contexto de código.

 Para recuperar el contexto del código de un identificador de ubicación del código, llame el [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) método.

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)