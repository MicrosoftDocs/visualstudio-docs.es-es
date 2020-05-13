---
title: IDebugDocument2::GetName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731961"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtiene el nombre del documento en uno de varios formularios.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parámetros
`gnType`\
[en] Valor de la [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeración que determina el tipo de nombre que se va a devolver.

`pbstrFileName`\
[fuera] Devuelve una cadena que contiene el nombre del documento.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método puede, por ejemplo, devolver el nombre del documento como un título o como un nombre de archivo o incluso parte de un nombre de archivo.

## <a name="see-also"></a>Vea también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
