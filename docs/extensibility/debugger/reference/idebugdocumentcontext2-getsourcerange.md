---
title: 'IDebugDocumentContext2:: Getsourcerange (| Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
[in, out] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición inicial. Establezca este argumento en un valor NULL si no se necesita esta información.

`pEndPosition`\
[in, out] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición final. Establezca este argumento en un valor NULL si no se necesita esta información.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un intervalo de origen es todo el intervalo de código fuente, desde la instrucción actual hasta justo después de la instrucción anterior que ha contribuido al código. El intervalo de origen se usa normalmente para mezclar instrucciones de código fuente, incluidos los comentarios, con código en la ventana Desensamblado.

 Para obtener el intervalo solo para las instrucciones de código contenidas en este contexto de documento, llame al método [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
