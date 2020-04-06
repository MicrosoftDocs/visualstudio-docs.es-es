---
title: IDebugPortSupplier2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724473"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Esta interfaz suministra puertos al administrador de depuración de sesión (SDM).

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un proveedor de puertos personalizado implementa esta interfaz para representar a un proveedor de puertos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
Una llamada `CoCreateInstance` a con un `GUID` proveedor de puerto devuelve esta interfaz (esta es la manera típica de obtener esta interfaz). Por ejemplo:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Una llamada a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) devuelve esta interfaz, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]que representa el proveedor de puerto actual que utiliza .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor de puertos que creó el puerto.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa una `IDebugPortSupplier` lista de `IEnumDebugPortSuppliers` interfaces (la interfaz se obtiene de [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa a todos los proveedores de puertos registrados con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Normalmente, un motor de depuración no interactúa con un proveedor de puertos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente `IDebugPortSupplier2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtiene el nombre del proveedor de puerto.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtiene el identificador de proveedor de puerto.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtiene un puerto de un proveedor de puertos.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera los puertos que ya existen.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Comprueba que un proveedor de puertos admite la adición de nuevos puertos.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Agrega un puerto.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Quita un puerto.|

## <a name="remarks"></a>Observaciones
Un proveedor de puertos puede identificarse por nombre e ID, agregar y quitar puertos y enumerar todos los puertos que proporciona el proveedor de puertos.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
