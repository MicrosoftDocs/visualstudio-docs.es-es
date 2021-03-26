---
description: Este método deshabilita explícitamente editar y continuar en este proceso (y todos los programas que contiene).
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f9c4a1e05cf7d4a98489daf0c2ee3377d54f417
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081625"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Este método deshabilita explícitamente editar y continuar en este proceso (y todos los programas que contiene). Un proveedor de Puerto personalizado siempre debe devolver `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parámetros
`reason`\
de Un valor de la enumeración [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

> [!NOTE]
> Un proveedor de Puerto personalizado siempre debe devolver `E_NOTIMPL` .

## <a name="remarks"></a>Observaciones
 Una vez que editar y continuar está deshabilitado para un proceso, solo se puede volver a habilitar reiniciando el proceso.

## <a name="see-also"></a>Consulte también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
