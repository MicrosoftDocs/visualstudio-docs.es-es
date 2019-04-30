---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302a911e58a23bdcd58bb054c1fc90c389fed6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865458"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Especifica las marcas de la información de depuración del módulo.

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

## <a name="members"></a>Miembros
 MIF_NONE Initialize o usar ninguno de los campos de la estructura.

 MIF_NAME Initialize o usar el `m_bstrName` campo el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura.

 MIF_URL Initialize o usar el `m_bstrUrl` campo el `MODULE_INFO` estructura.

 MIF_VERSION Initialize o usar el `m_bstrVersion` campo el `MODULE_INFO` estructura.

 MIF_DEBUGMESSAGE Initialize o usar el `m_bstrDebugMessage` campo el `MODULE_INFO` estructura.

 MIF_LOADADDRESS Initialize o usar el `m_addrLoadAddress` campo el `MODULE_INFO` estructura.

 MIF_PREFFEREDADDRESS Initialize o usar el `m_addrPreferredLoadAddress` campo el `MODULE_INFO` estructura.

 MIF_SIZE Initialize o usar el `m_dwSize` campo el `MODULE_INFO` estructura.

 MIF_LOADORDER Initialize o usar el `m_dwLoadOrder` campo el `MODULE_INFO` estructura.

 MIF_TIMESTAMP Initialize o usar el `m_TimeStamp` campo el `MODULE_INFO` estructura.

 MIF_URLSYMBOLLOCATION Initialize o usar el `m_bstrUrlSymbolLocation` campo el `MODULE_INFO` estructura.

 MIF_FLAGS Initialize o usar el `m_dwModuleFlags` campo el `MODULE_INFO` estructura.

 MIF_ALLFIELDS Initialize o usar todos los campos en el `MODULE_INFO` estructura.

## <a name="remarks"></a>Comentarios
 Estos valores se pasan como argumento a la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) método para indicar qué campos de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura deben inicializarse.

 Estos valores también se usan en el `MODULE_INFO` estructura para indicar qué campos se usan y válido.

 Estas marcas se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)