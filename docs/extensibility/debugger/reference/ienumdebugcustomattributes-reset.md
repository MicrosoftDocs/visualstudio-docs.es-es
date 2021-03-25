---
description: Restablece la secuencia de enumeración de atributos personalizados al principio.
title: 'IEnumDebugCustomAttributes:: RESET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b48e541f1f75f3ce7f0ef69e1e838cd54ffa19fa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080130"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Restablece la secuencia de enumeración al principio.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Después de llamar a este método, la siguiente llamada al método [siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Consulte también
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
