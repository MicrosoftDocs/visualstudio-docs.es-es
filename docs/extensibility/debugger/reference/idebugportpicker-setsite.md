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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d44c0ad0cef8777623f3393172e372ea4c33782a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204509"
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

## <a name="parameters"></a>Parámetros
`pSP`\
[in] Referencia a la interfaz del proveedor de servicios.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se llamará antes de llamar a ningún otro método.

## <a name="see-also"></a>Vea también
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)