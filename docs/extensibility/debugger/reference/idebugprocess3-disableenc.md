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
ms.openlocfilehash: 2cc26c9d2dae65d8bab0126be5a62b144ebf42b7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413298"
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

#### <a name="parameters"></a>Parámetros
 `reason`

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