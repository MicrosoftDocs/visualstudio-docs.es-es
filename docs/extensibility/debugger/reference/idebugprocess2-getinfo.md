---
description: Obtiene una descripción del proceso.
title: 'IDebugProcess2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01771f011df4e40b2323ef9cc44027f9456c2fbf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081846"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Obtiene una descripción del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parámetros
`Fields`\
de Combinación de valores de la enumeración [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) que especifica qué campos del `pProcessInfo` parámetro se van a rellenar.

`pProcessInfo`\
enuncia [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura que se rellena con una descripción del proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
