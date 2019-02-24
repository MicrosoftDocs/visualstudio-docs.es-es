---
title: IDebugProcessSecurity | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12c1cc5af90fa0ff337a105f6d3d7232b72ab6ac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695237"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` se implementa mediante un proveedor de puerto para advertir al usuario que no es seguro asociar al proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugProcessSecurity`.

|Método|Descripción|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario desde el proveedor del puerto.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte al usuario que no es seguro asociar al proceso de depuración.|

## <a name="remarks"></a>Comentarios
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario pueda cancelar si el proceso al que va a asociar puede considerarse no seguro.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Puertos](../../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)