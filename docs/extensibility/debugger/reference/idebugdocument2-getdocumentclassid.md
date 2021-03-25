---
description: Obtiene el identificador de clase del documento.
title: 'IDebugDocument2:: GetDocumentClassID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 829f0002a79f2fd5ec69f31ef4b59068bc5b5c05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066859"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Obtiene el identificador de clase del documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Parámetros
`pclsid` enuncia Devuelve un GUID que es el identificador de clase del documento.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El GUID de clase se puede usar para crear instancias de clases individuales cada una de las cuales representa un documento.

## <a name="see-also"></a>Consulte también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
