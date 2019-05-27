---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 65f79b73eaa9b97630cc3ef3e84e1ba4198835c9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202361"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Este método explícitamente deshabilita Editar y continuar en este proceso (y todos los programas contiene). Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.

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
[in] Un valor de la [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumeración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.

> [!NOTE]
> Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.

## <a name="remarks"></a>Comentarios
 Una vez que editar y continuar está deshabilitado para un proceso, puede volver a habilitar reiniciando el proceso.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)