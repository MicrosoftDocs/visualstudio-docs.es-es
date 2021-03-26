---
description: Obtiene el identificador de proceso del sistema.
title: 'IDebugProcess2:: GetPhysicalProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ec1f2340b744efe5620bd2876c5dbe8539e786f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081820"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
Obtiene el identificador de proceso del sistema.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPhysicalProcessId(
   AD_PROCESS_ID* pdwProcessId
);
```

```csharp
int GetPhysicalProcessId(
   AD_PROCESS_ID[] pdwProcessId
);
```

## <a name="parameters"></a>Parámetros
`pdwProcessId`\
enuncia [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura que se rellena con la información del identificador de proceso del sistema.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
