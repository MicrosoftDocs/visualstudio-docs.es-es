---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9c260ecefb2e8c295451eb1bab8ef2da98e002b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681990"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtiene el contexto del documento que corresponde a este contexto de código. El contexto del documento representa una posición en el archivo de origen que se corresponde con el código fuente que generó esta instrucción.

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

#### <a name="parameters"></a>Parámetros
 `ppSrcCxt`

 [out] Devuelve el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto que corresponde al contexto del código.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Por lo general, el contexto del documento puede considerarse como una posición en un archivo de código fuente mientras el contexto del código es una posición de una instrucción de código en un flujo de ejecución.

## <a name="see-also"></a>Vea también
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)