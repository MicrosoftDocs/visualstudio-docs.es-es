---
title: Implementar y registrar un proveedor de puerto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 253289862ae341e0682f5fe19616720e74799a1d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719865"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementar y registrar un proveedor de puerto
El rol de un proveedor de puerto es realizar un seguimiento y proporcionar los puertos, lo que a su vez administración procesos. Cuando se debe crear un puerto, el proveedor del puerto se crea una instancia mediante el comando CoCreate con el GUID del proveedor de puerto (el Administrador de depuración de sesión [SDM] utilizará el proveedor del puerto que seleccionó el usuario o el proveedor del puerto especificado por el sistema del proyecto). A continuación, llama el SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si se puede agregar ningún puerto. Si se puede agregar un puerto, se solicita un nuevo puerto mediante una llamada a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasándole un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describe el puerto. `AddPort` Devuelve un nuevo puerto representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz.

## <a name="discussion"></a>Discusión
 Se crea un puerto mediante un proveedor de puerto, que está asociado a un servidor de la máquina o de depuración. Un servidor enumera sus proveedores de puertos a través de la[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método y un proveedor de puerto enumera sus puertos a través de la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.

 Además del registro de COM típico, un proveedor de puerto debe registrarse con Visual Studio, coloque su CLSID y su nombre en ubicaciones específicas del registro. Llama una función de aplicación auxiliar de depuración SDK `SetMetric` controla esta tarea rutinaria: se llama una vez por cada elemento se registre, así:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Un proveedor de puerto anula su propio registro mediante una llamada a `RemoveMetric` (función de otro SDK de depuración auxiliar) una vez para cada elemento que se registró, así:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
>  El [aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` se definen las funciones estáticas en *dbgmetric.h* y compilado en *ad2de.lib*. El `metrictypePortSupplier`, `metricCLSID`, y `metricName` aplicaciones auxiliares también se definen en *dbgmetric.h*.

 Un proveedor de puerto puede proporcionar su nombre y GUID mediante los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.

## <a name="see-also"></a>Vea también
- [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)