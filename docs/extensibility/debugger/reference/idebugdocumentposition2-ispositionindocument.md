---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab4792427a98f97fcd50d4b39c2bb332527a0942
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333407"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Determina si la posición del documento se encuentra en el documento especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Parámetros
`pDoc`\
[in] El [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa el candidato de documento que contiene.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se utiliza principalmente en establecer puntos de interrupción [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaces. Como se carguen documentos, la posición del punto de interrupción se llama para determinar si el documento contiene esta posición.

## <a name="see-also"></a>Vea también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)