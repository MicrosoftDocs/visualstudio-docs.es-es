---
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7113cfead52348a1d1a85973b90014ca53226ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850731"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Describe los atributos de un documento.

## <a name="syntax"></a>Sintaxis

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Members
 `TEXT_DOC_ATTR_READONLY_2`\
 Indica que el documento es de solo lectura.

## <a name="remarks"></a>Notas

> [!NOTE]
> En realidad, este valor no está definido en el ensamblado para C#. En su lugar, debe copiar la definición en el archivo de código fuente.

 Se pasa como argumento al método [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
