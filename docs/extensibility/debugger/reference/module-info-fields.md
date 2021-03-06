---
description: Especifica las marcas para la información del módulo de depuración.
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc27420fc598d174b8e71c5ed3edd879a4a30d9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222372"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Especifica las marcas para la información del módulo de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Fields
 `MIF_NONE`\
 Inicializar/usar ninguno de los campos de la estructura.

 `MIF_NAME`\
 Inicialice o use el `m_bstrName` campo de la estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 `MIF_URL`\
 Inicializar/usar el `m_bstrUrl` campo en la `MODULE_INFO` estructura.

 `MIF_VERSION`\
 Inicializar/usar el `m_bstrVersion` campo en la `MODULE_INFO` estructura.

 `MIF_DEBUGMESSAGE`\
 Inicializar/usar el `m_bstrDebugMessage` campo en la `MODULE_INFO` estructura.

 `MIF_LOADADDRESS`\
 Inicializar/usar el `m_addrLoadAddress` campo en la `MODULE_INFO` estructura.

 `MIF_PREFFEREDADDRESS`\
 Inicializar/usar el `m_addrPreferredLoadAddress` campo en la `MODULE_INFO` estructura.

 `MIF_SIZE`\
 Inicializar/usar el `m_dwSize` campo en la `MODULE_INFO` estructura.

 `MIF_LOADORDER`\
 Inicializar/usar el `m_dwLoadOrder` campo en la `MODULE_INFO` estructura.

 `MIF_TIMESTAMP`\
 Inicializar/usar el `m_TimeStamp` campo en la `MODULE_INFO` estructura.

 `MIF_URLSYMBOLLOCATION`\
 Inicializar/usar el `m_bstrUrlSymbolLocation` campo en la `MODULE_INFO` estructura.

 `MIF_FLAGS`\
 Inicializar/usar el `m_dwModuleFlags` campo en la `MODULE_INFO` estructura.

 `MIF_ALLFIELDS`\
 Inicialice o utilice todos los campos de la `MODULE_INFO` estructura.

## <a name="remarks"></a>Observaciones
 Estos valores se pasan como un argumento al método [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) para indicar qué campos de la estructura de [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) se van a inicializar.

 Estos valores también se usan en la `MODULE_INFO` estructura para indicar qué campos se usan y son válidos.

 Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
