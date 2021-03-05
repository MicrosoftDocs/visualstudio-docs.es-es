---
description: Especifica cómo interpretar un identificador de proceso en la estructura de AD_PROCESS_ID.
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f56ca1db0462a85bd68b193147f5dd3a46c6bee9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164349"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Especifica cómo interpretar un identificador de proceso en la estructura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`AD_PROCESS_ID_SYSTEM`\
El identificador de proceso es un identificador de sistema. Utilice el `ProcessId.dwProcessId` campo de la estructura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

`AD_PROCESS_ID_GUID`\
El ID. de proceso es un GUID. Use el `ProcessId.guidProcessId` campo de la `AD_PROCESS_ID` estructura.

## <a name="remarks"></a>Observaciones
Se usa para el `ProcessIdType` miembro de la estructura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) para identificar el tipo de identificador de proceso contenido en la estructura. Determina cómo se interpreta la `ProcessId` Unión en la estructura.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
