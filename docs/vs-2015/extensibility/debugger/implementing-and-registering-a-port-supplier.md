---
title: Implementar y registrar un proveedor de puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3844d6beca76781f741bfbe0c6bff71923075d36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728939"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementación y registro de un proveedor de puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El rol de un proveedor de puerto es realizar un seguimiento y proporcionar los puertos, lo que a su vez administración procesos. En el momento en que se debe crear un puerto, se crea una instancia del proveedor del puerto mediante CoCreate con el GUID del proveedor de puerto (el Administrador de depuración de sesión [SDM] usará el proveedor del puerto seleccionados por el usuario o el proveedor del puerto especificado por el sistema del proyecto). A continuación, se llamará el SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si se puede agregar ningún puerto. Si se puede agregar un puerto, se solicita un nuevo puerto mediante una llamada a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasándole un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describe el puerto. `AddPort` Devuelve un nuevo puerto representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz.  
  
## <a name="discussion"></a>Explicación  
 Se crea un puerto mediante un proveedor de puerto, que está asociado a su vez a un servidor de la máquina o de depuración. Un servidor puede enumerar sus proveedores de puertos a través de la[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método y un proveedor de puerto pueden enumerar sus puertos a través de la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.  
  
 Además del registro de COM típico, un proveedor de puerto debe registrarse con Visual Studio, coloque su CLSID y su nombre en ubicaciones específicas del registro. Llama una función de aplicación auxiliar de depuración SDK `SetMetric` controla esta tarea rutinaria: se llama una vez por cada elemento se registre, así:  
  
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
  
 Un proveedor de puerto anula su propio registro mediante una llamada a `RemoveMetric` (función de otro SDK de depuración auxiliar) una vez para cada elemento que se registró, así:  
  
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
>  El [aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` son funciones estáticas definido en dbgmetric.h y se compilan en ad2de.lib. El `metrictypePortSupplier`, `metricCLSID`, y `metricName` aplicaciones auxiliares también se definen en dbgmetric.h.  
  
 Un proveedor de puerto puede proporcionar su nombre y GUID mediante los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)

