---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0964c94334ca0815b4410f6858dca5502b2f8a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678467"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Establece el proveedor de servicios.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

#### <a name="parameters"></a>Parámetros
 `pSP`

 [in] Referencia a la interfaz del proveedor de servicios.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se llamará antes de llamar a ningún otro método.

## <a name="see-also"></a>Vea también
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)