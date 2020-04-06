---
title: IDebugDocumentContext2::GetSourceRange ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731792"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Obtiene el intervalo de código fuente de este contexto de documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parámetros
`pBegPosition`\
[adentro, fuera] Una [estructura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que se rellena con la posición inicial. Establezca este argumento en un valor nulo si esta información no es necesaria.

`pEndPosition`\
[adentro, fuera] Una [estructura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que se rellena con la posición final. Establezca este argumento en un valor nulo si esta información no es necesaria.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un intervalo de código fuente es todo el intervalo de código fuente, desde la instrucción actual hasta justo después de la instrucción anterior que aportó código. El intervalo de origen se utiliza normalmente para mezclar instrucciones de origen, incluidos comentarios, con código en la ventana de desensamblado.

 Para obtener el intervalo solo para las instrucciones de código contenidas en este contexto de documento, llame a la [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) método.

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
