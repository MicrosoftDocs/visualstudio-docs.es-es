---
description: Esta interfaz proporciona puertos al administrador de depuración de sesión (SDM).
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd28e261c9c74601bd88f2d84e1296a1ed508f37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072031"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Esta interfaz proporciona puertos al administrador de depuración de sesión (SDM).

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un proveedor de Puerto personalizado implementa esta interfaz para representar un proveedor de puerto.

## <a name="notes-for-callers"></a>Notas para llamadores
Una llamada a `CoCreateInstance` con el de un proveedor de puerto `GUID` devuelve esta interfaz (esta es la forma habitual de obtener esta interfaz). Por ejemplo:

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

Una llamada a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor de puerto actual utilizado por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor del puerto que creó el puerto.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa una lista de `IDebugPortSupplier` interfaces (la `IEnumDebugPortSuppliers` interfaz se obtiene de [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa todos los proveedores de puertos registrados con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Normalmente, un motor de depuración no interactúa con un proveedor de puertos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDebugPortSupplier2` .

|Método|Descripción|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtiene el nombre del proveedor del puerto.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtiene el identificador del proveedor del puerto.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtiene un puerto de un proveedor de puerto.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera los puertos que ya existen.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Comprueba que un proveedor de puertos permite agregar nuevos puertos.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Agrega un puerto.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Quita un puerto.|

## <a name="remarks"></a>Observaciones
Un proveedor de puertos puede identificarse por el nombre y el identificador, agregar y quitar puertos y enumerar todos los puertos proporcionados por el proveedor del puerto.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
