---
description: Obtiene el contexto del documento que corresponde a este contexto de código.
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b67e76c8cc8719c77c88c8b93ca667c3a025a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164167"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtiene el contexto del documento que corresponde a este contexto de código. El contexto del documento representa una posición en el archivo de código fuente que corresponde al código fuente que generó esta instrucción.

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
enuncia Devuelve el objeto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que corresponde al contexto del código. Si `S_OK` se devuelve, este no debe ser `null` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un motor de depuración debe devolver un código de error como `E_FAIL` cuando el `out` parámetro es como `null` cuando el contexto del código no tiene ninguna posición de origen asociada.

## <a name="remarks"></a>Observaciones
 Por lo general, el contexto del documento se puede considerar como una posición en un archivo de código fuente mientras que el contexto del código es una posición de una instrucción de código en una secuencia de ejecución.

## <a name="see-also"></a>Consulte también
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
