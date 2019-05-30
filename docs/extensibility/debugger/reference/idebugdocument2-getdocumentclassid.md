---
title: IDebugDocument2::GetDocumentClassID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51a4ed842a2f65f37abf6f83ac70d6ce03b9a2e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310284"
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
`pclsid` [out] Devuelve un GUID que es el identificador de clase del documento.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El GUID de clase puede usarse para crear instancias de clases individuales de cada uno de los cuales representa un documento.

## <a name="see-also"></a>Vea también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)