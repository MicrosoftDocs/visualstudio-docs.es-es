---
title: IDebugProcessSecurity ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723194"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`es implementado por un proveedor de puertos para advertir al usuario que adjuntar al proceso no es seguro.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugProcessSecurity`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario del proveedor de puertos.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte a un usuario que adjuntar al proceso de depuración no es seguro.|

## <a name="remarks"></a>Observaciones
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario cancele si el proceso al que se está adjuntando puede considerarse no seguro.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Puertos](../../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
