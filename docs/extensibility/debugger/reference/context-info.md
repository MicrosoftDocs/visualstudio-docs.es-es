---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a95808383d4d75810f17b4da121a11025b6f894
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912988"
---
# <a name="context_info"></a>CONTEXT_INFO
Esta estructura describe un contexto de memoria o de código.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Members
`dwFields`\
Una combinación de marcas de la enumeración [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) que especifica qué campos se rellenan<strong>.</strong>

`bstrModuleUrl`\
Nombre del módulo donde se encuentra el contexto.

`bstrFunction`\
Nombre de la función donde se encuentra el contexto.

`posFunctionOffset`\
Estructura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que identifica el desplazamiento de línea y columna de la función asociada al contexto del código.

`bstrAddress`\
Dirección en el código donde se encuentra el contexto especificado.

`bstrAddressOffset`\
Desplazamiento de la dirección en el código donde se encuentra el contexto especificado.

`bstrAddressAbsolute`\
Dirección absoluta en memoria donde se encuentra el contexto especificado.

## <a name="remarks"></a>Notas
Esta estructura se devuelve desde una llamada al método [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .

Un uso típico de esta estructura es la compatibilidad de una ventana de depuración de **memoria** .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
