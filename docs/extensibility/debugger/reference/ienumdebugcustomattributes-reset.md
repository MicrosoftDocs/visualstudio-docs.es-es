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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3393f2b87043345156337976ed12d10928572d2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226896"
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
