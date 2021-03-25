---
description: Devuelve un identificador de ubicación de código para un contexto de código determinado.
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f68ee6ff0495fe36d8de8ccf0e3c2c81f3d05ac5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067093"
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
de Un objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que se va a convertir en un identificador.

`puCodeLocationId` enuncia Devuelve el identificador de ubicación del código. Vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_CODE_CONTEXT_OUT_OF_SCOPE` si el contexto del código es válido pero está fuera del ámbito.

## <a name="remarks"></a>Observaciones
 El identificador de ubicación del código es específico del motor DE depuración (DE) que admite el desensamblado. La clase usa internamente este identificador de ubicación para realizar el seguimiento de las posiciones en el código y suele ser una dirección o desplazamiento de algún tipo. El único requisito es que si el contexto de código de una ubicación es menor que el contexto de código de otra ubicación, el identificador de ubicación de código correspondiente del primer contexto de código también debe ser menor que el identificador de ubicación de código del segundo contexto de código.

 Para recuperar el contexto del código de un identificador de ubicación de código, llame al método [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>Consulte también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
