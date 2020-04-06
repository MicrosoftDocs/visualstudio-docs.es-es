---
title: MODULE_INFO_FIELDS de la casa de la inser Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714328"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Especifica los indicadores para la información del módulo de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_MODULE_INFO_FIELDS { 
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
public enum enum_MODULE_INFO_FIELDS { 
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
 Inicializar/utilizar ninguno de los campos de la estructura.

 `MIF_NAME`\
 Inicializar/utilizar `m_bstrName` el campo de la estructura [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Inicializar/utilizar `m_bstrUrl` el campo `MODULE_INFO` de la estructura.

 `MIF_VERSION`\
 Inicializar/utilizar `m_bstrVersion` el campo `MODULE_INFO` de la estructura.

 `MIF_DEBUGMESSAGE`\
 Inicializar/utilizar `m_bstrDebugMessage` el campo `MODULE_INFO` de la estructura.

 `MIF_LOADADDRESS`\
 Inicializar/utilizar `m_addrLoadAddress` el campo `MODULE_INFO` de la estructura.

 `MIF_PREFFEREDADDRESS`\
 Inicializar/utilizar `m_addrPreferredLoadAddress` el campo `MODULE_INFO` de la estructura.

 `MIF_SIZE`\
 Inicializar/utilizar `m_dwSize` el campo `MODULE_INFO` de la estructura.

 `MIF_LOADORDER`\
 Inicializar/utilizar `m_dwLoadOrder` el campo `MODULE_INFO` de la estructura.

 `MIF_TIMESTAMP`\
 Inicializar/utilizar `m_TimeStamp` el campo `MODULE_INFO` de la estructura.

 `MIF_URLSYMBOLLOCATION`\
 Inicializar/utilizar `m_bstrUrlSymbolLocation` el campo `MODULE_INFO` de la estructura.

 `MIF_FLAGS`\
 Inicializar/utilizar `m_dwModuleFlags` el campo `MODULE_INFO` de la estructura.

 `MIF_ALLFIELDS`\
 Inicializar/utilizar todos los campos `MODULE_INFO` de la estructura.

## <a name="remarks"></a>Observaciones
 Estos valores se pasan como argumento al método [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) para indicar qué campos de la estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) se van a inicializar.

 Estos valores también se `MODULE_INFO` utilizan en la estructura para indicar qué campos se utilizan y son válidos.

 Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
