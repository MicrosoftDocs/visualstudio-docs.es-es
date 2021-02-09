---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 451a6ea5334006bb23e8961595f4de85c985b8ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895952"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Especifica el tipo de información que se va a recuperar para un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Campos
 `PIF_FILE_NAME`\
 Inicialice o utilice el `bstrFileName` campo de la estructura de [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

 `PIF_BASE_NAME`\
 Inicialice o use el `bstrBaseName` campo de la `PROCESS_INFO` estructura.

 `PIF_TITLE`\
 Inicialice o use el `bstrTitle` campo de la `PROCESS_INFO` estructura.

 `PIF_PROCESS_ID`\
 Inicialice o use el `ProcessId` campo de la `PROCESS_INFO` estructura.

 `PIF_SESSION_ID`\
 Inicialice o use el `dwSessionId` campo de la `PROCESS_INFO` estructura.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicialice o use el `bstrAttachedSessionName` campo de la `PROCESS_INFO` estructura.

 `PIF_CREATION_TIME`\
 Inicialice o use el `CreationTime` campo de la `PROCESS_INFO` estructura.

 `PIF_FLAGS`\
 Inicialice o use el `Flags` campo de la `PROCESS_INFO` estructura.

 `PIF_ALL`\
 Rellena todos los campos.

## <a name="remarks"></a>Notas
 Se pasa al método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) para indicar qué campos de la estructura de [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) se van a inicializar.

 También se utiliza en `Fields` el campo de la `PROCESS_INFO` estructura para indicar qué campos se usan y son válidos.

 Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
