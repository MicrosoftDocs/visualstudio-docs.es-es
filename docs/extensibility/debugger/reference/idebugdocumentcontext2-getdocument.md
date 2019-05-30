---
title: IDebugDocumentContext2::GetDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ce07bd2274bc2a4881acd98fb73266fc90c7bd8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341278"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
Obtiene el documento que contiene el contexto de este documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDocument
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDocument
);
```

## <a name="parameters"></a>Parámetros
`ppDocument`\
[out] Devuelve un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa el documento que contiene el contexto de este documento.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método es para los motores de depuración que proporcionan los documentos directamente en el IDE. En caso contrario, este método debe devolver `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)