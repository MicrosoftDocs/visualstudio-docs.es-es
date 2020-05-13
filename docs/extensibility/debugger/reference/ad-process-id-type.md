---
title: AD_PROCESS_ID_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738192"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Especifica cómo interpretar un identificador de proceso en la estructura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Fields
`AD_PROCESS_ID_SYSTEM`\
El identificador de proceso es un identificador del sistema. Utilice `ProcessId.dwProcessId` el campo de la estructura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

`AD_PROCESS_ID_GUID`\
El identificador de proceso es un GUID. Utilice `ProcessId.guidProcessId` el campo `AD_PROCESS_ID` de la estructura.

## <a name="remarks"></a>Observaciones
Se utiliza `ProcessIdType` para el miembro de la [estructura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) para identificar el tipo de identificador de proceso que se encuentra en la estructura. Determina cómo interpretar `ProcessId` la unión en la estructura.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
