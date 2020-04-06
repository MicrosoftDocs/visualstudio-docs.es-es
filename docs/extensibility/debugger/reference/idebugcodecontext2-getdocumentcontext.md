---
title: IDebugCodeContext2::GetDocumentContext ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734347"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtiene el contexto de documento que corresponde a este contexto de código. El contexto del documento representa una posición en el archivo de origen que corresponde al código fuente que generó esta instrucción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parámetros
`ppSrcCxt`\
[fuera] Devuelve el objeto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que corresponde al contexto de código. Si `S_OK` se devuelve, ths`null`debe ser non- .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un motor de depuración debe `E_FAIL` devolver `out` un `null` código de error, como cuando el parámetro es como cuando el contexto de código no tiene ninguna posición de origen asociada.

## <a name="remarks"></a>Observaciones
 Por lo general, el contexto del documento se puede considerar como una posición en un archivo de código fuente, mientras que el contexto de código es una posición de una instrucción de código en una secuencia de ejecución.

## <a name="see-also"></a>Vea también
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
