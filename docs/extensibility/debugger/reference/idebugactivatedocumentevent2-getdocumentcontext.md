---
description: Obtiene el contexto del documento que describe la posición en el documento que el paquete de depuración va a activar.
title: 'IDebugActivateDocumentEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 680382e43feee9298a2de99933847ea633982a15
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154943"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Obtiene el contexto del documento que describe la posición en el documento que el paquete de depuración va a activar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parámetros
`ppDocContext`\
enuncia Devuelve un objeto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que representa una posición en un documento de archivo de código fuente.

## <a name="remarks"></a>Observaciones
 Esta posición podría usarse para mostrar el símbolo de intercalación, por ejemplo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
