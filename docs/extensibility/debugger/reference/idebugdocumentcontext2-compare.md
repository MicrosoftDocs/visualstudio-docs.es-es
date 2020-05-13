---
title: IDebugDocumentContext2::Compare ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731884"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento con una matriz determinada de contextos de documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parámetros
`compare`\
[en] Valor de la [enumeración DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) que especifica el tipo de comparación.

`rgpDocContextSet`\
[en] Matriz de [objetos IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que representan los contextos de documento con los que se comparan.

`dwDocContextSetLen`\
[en] La longitud de la matriz de contextos de documento que se van a comparar.

`pdwDocContext`\
[fuera] Devuelve el índice `rgpDocContextSet` en la matriz del primer contexto de documento que satisface la comparación.

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si se ha encontrado una coincidencia. Devuelve `S_FALSE` si no se encontró ninguna coincidencia. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que se pasan en la matriz deben implementarse por el mismo motor de depuración que implementa el `IDebugDocumentContext2` objeto que se llama en; de lo contrario, la comparación no es válida.

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
