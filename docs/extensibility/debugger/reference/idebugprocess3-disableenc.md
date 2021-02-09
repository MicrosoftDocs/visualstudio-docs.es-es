---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5cfd425e6b992d8d933edd45f27d6fb4c8161a1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891051"
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

## <a name="remarks"></a>Notas
 Una vez que editar y continuar está deshabilitado para un proceso, solo se puede volver a habilitar reiniciando el proceso.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
