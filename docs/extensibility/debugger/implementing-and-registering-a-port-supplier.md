---
title: Implementación y Registro de un Proveedor de Puertos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738532"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementar y registrar un proveedor portuario
La función de un proveedor de puertos es realizar un seguimiento y suministrar puertos, que a su vez gestionan los procesos. Cuando es necesario crear un puerto, se crea una instancia del proveedor de puertos mediante CoCreate con el GUID del proveedor de puertos (el administrador de depuración de sesión [SDM] usará el proveedor de puertos seleccionado por el usuario o el proveedor de puerto especificado por el sistema de proyecto). El SDM entonces llama a [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si se puede agregar algún puerto. Si se puede agregar un puerto, se solicita un nuevo puerto llamando a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasándole un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describe el puerto. `AddPort`devuelve un nuevo puerto representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz.

## <a name="discussion"></a>Discusión
 Un puerto es creado por un proveedor de puertos, que está asociado a una máquina o servidor de depuración. Un servidor enumera sus proveedores de puertos a través de la[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método y un proveedor de puertoenumera sus puertos a través de la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.

 Además del registro COM típico, un proveedor de puertos debe registrarse en Visual Studio colocando su CLSID y el nombre en ubicaciones de registro específicas. Una función auxiliar `SetMetric` de SDK de depuración denominada controla esta tarea: se llama una vez para cada elemento que se va a registrar, por lo tanto:

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

 Un proveedor de puertos `RemoveMetric` se anula el registro llamando a sí mismo llamando a (otra función auxiliar del SDK de depuración) una vez para cada elemento que se registró, por lo tanto:

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
> Las [aplicaciones auxiliares del SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` son funciones estáticas definidas en *dbgmetric.h* y compiladas en *ad2de.lib*. Las `metrictypePortSupplier` `metricCLSID`aplicaciones, `metricName` , y helper también se definen en *dbgmetric.h*.

 Un proveedor de puertos puede proporcionar su nombre y GUID a través de los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.

## <a name="see-also"></a>Vea también
- [Implementar un proveedor portuario](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Ayudantes del SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Proveedores portuarios](../../extensibility/debugger/port-suppliers.md)
