---
description: Determina si la posición del documento está contenida en el documento especificado.
title: 'IDebugDocumentPosition2:: IsPositionInDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab3d00df9883da93d0d8121433b962d365a408e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066417"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Determina si la posición del documento está contenida en el documento especificado.

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
de El objeto [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que representa el candidato del documento contenedor.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método se utiliza principalmente en el establecimiento de puntos de interrupción en interfaces [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) . A medida que se cargan los documentos, se llama a la posición del punto de interrupción para determinar si el documento contiene esta posición.

## <a name="see-also"></a>Consulte también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
