---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe9a1854fe5583d001e1dc156bfad5833fd1c08f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309454"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Especifica qué tipo de información que se va a recuperar de un proceso.

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

## <a name="fields"></a>Campos
 `PIF_FILE_NAME`\
 Inicializar o usar el `bstrFileName` campo de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura.

 `PIF_BASE_NAME`\
 Inicializar o usar el `bstrBaseName` campo de la `PROCESS_INFO` estructura.

 `PIF_TITLE`\
 Inicializar o usar el `bstrTitle` campo de la `PROCESS_INFO` estructura.

 `PIF_PROCESS_ID`\
 Inicializar o usar el `ProcessId` campo de la `PROCESS_INFO` estructura.

 `PIF_SESSION_ID`\
 Inicializar o usar el `dwSessionId` campo de la `PROCESS_INFO` estructura.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicializar o usar el `bstrAttachedSessionName` campo de la `PROCESS_INFO` estructura.

 `PIF_CREATION_TIME`\
 Inicializar o usar el `CreationTime` campo de la `PROCESS_INFO` estructura.

 `PIF_FLAGS`\
 Inicializar o usar el `Flags` campo de la `PROCESS_INFO` estructura.

 `PIF_ALL`\
 Rellena todos los campos.

## <a name="remarks"></a>Comentarios
 Pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método para indicar qué campos de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura deben inicializarse.

 También se usa en `Fields` campo de la `PROCESS_INFO` estructura para indicar qué campos se usan y válido.

 Estas marcas se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)