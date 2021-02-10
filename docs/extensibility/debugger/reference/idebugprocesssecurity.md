---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c6807ff64d8acf44551fa12fcb79199d3817373
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933029"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` lo implementa un proveedor de puerto para advertir al usuario de que la asociación al proceso no es segura.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProcessSecurity` .

|Método|Descripción|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario del proveedor del puerto.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte que un usuario que se asocia al proceso de depuración no es seguro.|

## <a name="remarks"></a>Notas
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario cancele si el proceso al que se va a adjuntar se puede considerar no seguro.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Puertos](../../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
