---
title: Implementación y registro de un proveedor de Puerto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843115"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementación y registro de un proveedor de puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El rol de un proveedor de puerto es realizar un seguimiento de los puertos y proporcionarlos, que a su vez administran los procesos. En el momento en que se debe crear un puerto, se crea una instancia del proveedor del puerto mediante CoCreate con el GUID del proveedor del puerto (el administrador de depuración de la sesión [SDM] usará el proveedor del puerto seleccionado por el usuario o el proveedor del puerto especificado por el sistema del proyecto). Después, el SDM llamará a [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si se pueden agregar puertos. Si se puede Agregar un puerto, se solicita un nuevo puerto llamando a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasándole un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describa el puerto. `AddPort` devolverá un nuevo puerto representado por una interfaz [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Debate  
 Un proveedor de Puerto crea un puerto que, a su vez, está asociado a un servidor de depuración o equipo. Un servidor puede enumerar sus proveedores de puertos a través del método[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) y un proveedor de puertos puede enumerar sus puertos a través del método [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Además del registro COM típico, un proveedor de puerto debe registrarse en Visual Studio colocando su CLSID y el nombre en ubicaciones específicas del registro. Una función auxiliar del SDK de depuración denominada `SetMetric` controla esta tarea: se llama una vez para cada elemento que se va a registrar, por lo que:  
  
```cpp#  
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
  
 Un proveedor de puertos anula su registro llamando a `RemoveMetric` (otra función auxiliar del SDK de depuración) una vez para cada elemento que se registró, por lo que:  
  
```cpp#  
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
> Las [aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` son funciones estáticas definidas en dbgmetric. h y compiladas en ad2de. lib. Las `metrictypePortSupplier` `metricCLSID` `metricName` aplicaciones auxiliares, y también se definen en dbgmetric. h.  
  
 Un proveedor de puertos puede proporcionar su nombre y GUID a través de los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Consulte también  
 [Implementación de un proveedor de Puerto](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)
