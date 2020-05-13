---
title: PROCESS_INFO_FIELDS de la página de la inser Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714013"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Se especificó qué tipo de información se va a recuperar para un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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

## <a name="fields"></a>Fields
 `PIF_FILE_NAME`\
 Inicializar/utilizar `bstrFileName` el campo de la [estructura PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

 `PIF_BASE_NAME`\
 Inicializar/utilizar `bstrBaseName` el campo `PROCESS_INFO` de la estructura.

 `PIF_TITLE`\
 Inicializar/utilizar `bstrTitle` el campo `PROCESS_INFO` de la estructura.

 `PIF_PROCESS_ID`\
 Inicializar/utilizar `ProcessId` el campo `PROCESS_INFO` de la estructura.

 `PIF_SESSION_ID`\
 Inicializar/utilizar `dwSessionId` el campo `PROCESS_INFO` de la estructura.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicializar/utilizar `bstrAttachedSessionName` el campo `PROCESS_INFO` de la estructura.

 `PIF_CREATION_TIME`\
 Inicializar/utilizar `CreationTime` el campo `PROCESS_INFO` de la estructura.

 `PIF_FLAGS`\
 Inicializar/utilizar `Flags` el campo `PROCESS_INFO` de la estructura.

 `PIF_ALL`\
 Rellena todos los campos.

## <a name="remarks"></a>Observaciones
 Se pasa al método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) para indicar qué campos de la [estructura PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) se van a inicializar.

 También se `Fields` utiliza `PROCESS_INFO` en el campo de la estructura para indicar qué campos se utilizan y son válidos.

 Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
