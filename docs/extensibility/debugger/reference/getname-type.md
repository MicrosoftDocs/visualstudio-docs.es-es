---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736676"
---
# <a name="getname_type"></a>GETNAME_TYPE
Especifica el tipo de nombre de los archivos que se van a recuperar.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Campos
`GN_NAME`\
Especifica un nombre descriptivo del documento o contexto.

`GN_FILENAME`\
Especifica la ruta de acceso completa del documento o contexto.

`GN_BASENAME`\
Especifica un nombre de archivo base en lugar de una ruta de acceso completa del documento o contexto.

`GN_MONIKERNAME`\
Especifica un nombre único del documento o contexto en forma de moniker.

`GN_URL`\
Especifica un nombre de dirección URL del documento o contexto.

`GN_TITLE`\
Especifica el título del documento, si existe.

`GN_STARTPAGEURL`\
Obtiene la dirección URL de la página de inicio de los procesos.

## <a name="remarks"></a>Observaciones
Estos valores se pasan como parámetros a los métodos [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)y [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) para especificar el tipo de nombre que se va a devolver.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
