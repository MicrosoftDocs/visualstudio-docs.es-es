---
title: IDebugDocumentTextEvents2::onRemoveText ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 744a6c769673acdc383999392cde88d255ad8142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731421"
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
Notifica al paquete de depuración que el texto se ha quitado del documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT onRemoveText( 
   TEXT_POSITION pos,
   DWORD         dwNumToRemove
);
```

```csharp
int onRemoveText( 
   enum_TEXT_POSITION pos,
   uint               dwNumToRemove
);
```

## <a name="parameters"></a>Parámetros
`pos`\
[en] Una [estructura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que indica dónde se eliminó el texto.

`dwNumToRemove`\
[en] Especifica el número de caracteres de texto que se quitaron.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
