---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 959d909d0c777110905aff3b11c8c29d27d628dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880767"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento con una matriz de contextos de documento determinada.

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
de Un valor de la enumeración [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) que especifica el tipo de comparación.

`rgpDocContextSet`\
de Matriz de objetos [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que representan los contextos de documento que se comparan.

`dwDocContextSetLen`\
de Longitud de la matriz de contextos de documento que se va a comparar.

`pdwDocContext`\
enuncia Devuelve el índice de la `rgpDocContextSet` matriz del primer contexto del documento que satisface la comparación.

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si se encontró una coincidencia. Devuelve `S_FALSE` si no se encontró ninguna coincidencia. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Los objetos [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que se pasan en la matriz deben ser implementados por el mismo motor de depuración que implementa el `IDebugDocumentContext2` objeto al que se llama; de lo contrario, la comparación no es válida.

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
