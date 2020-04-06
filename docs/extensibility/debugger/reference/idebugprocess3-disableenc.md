---
title: IDebugProcess3::DisableENC ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723735"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Este método deshabilita explícitamente Editar y continuar en este proceso (y todos los programas que contiene). Un proveedor de puerto `E_NOTIMPL`personalizado siempre debe devolver .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parámetros
`reason`\
[en] Un valor de la [enumeración EncUnavailableReason.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

> [!NOTE]
> Un proveedor de puerto `E_NOTIMPL`personalizado siempre debe devolver .

## <a name="remarks"></a>Observaciones
 Una vez que Editar y continuar está deshabilitado para un proceso, solo se puede volver a habilitar reiniciando el proceso.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
