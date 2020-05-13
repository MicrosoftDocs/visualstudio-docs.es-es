---
title: IDebugProcess2::GetInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f437c1a15b136d08ea7e57987c346844044228c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724027"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Obtiene una descripción del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parámetros
`Fields`\
[en] Una combinación de valores de la [enumeración PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) que especifica qué campos del `pProcessInfo` parámetro se deben rellenar.

`pProcessInfo`\
[fuera] Una [estructura PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) que se rellena con una descripción del proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
