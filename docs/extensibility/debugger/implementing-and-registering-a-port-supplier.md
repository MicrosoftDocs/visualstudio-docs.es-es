---
title: Implementar y registrar un proveedor del puerto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementar y registrar un proveedor de puerto
El rol de un proveedor de puerto es realizar un seguimiento y proporcionar puertos, lo que a su vez administración procesos. En el momento en que se debe crear un puerto, se crea una instancia del proveedor del puerto con CoCreate GUID del proveedor de puerto (el Administrador de sesión de depuración [SDM] va a usar el proveedor del puerto seleccionado por el usuario o el proveedor del puerto especificado por el sistema del proyecto). El SDM, a continuación, llame a [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si se puede agregar ninguno de los puertos. Si se puede agregar un puerto, se solicita un nuevo puerto mediante una llamada a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasarle una [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describe el puerto. `AddPort`Devuelve un nuevo puerto representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz.  
  
## <a name="discussion"></a>Explicación  
 Se crea un puerto por un proveedor de puerto, que está asociado a su vez a un servidor de la máquina o de depuración. Un servidor puede enumerar sus proveedores de puerto a través de la[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método y un proveedor de puerto pueden enumerar sus puertos a través de la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.  
  
 Además el registro de COM típico, un proveedor de puerto debe registrarse con Visual Studio, coloque su CLSID y el nombre en ubicaciones del Registro específica. Llama a una función de aplicación auxiliar de SDK de depuración `SetMetric` controla esta tarea ardua: se llama una vez por cada elemento se registre, por lo tanto:  
  
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
  
 Un proveedor de puerto anula su propio registro mediante una llamada a `RemoveMetric` (otra función de aplicación auxiliar de SDK de depuración) una vez para cada elemento que se haya registrado, por lo tanto:  
  
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
>  El [aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` son funciones estáticas definidas en dbgmetric.h y se compilan en ad2de.lib. El `metrictypePortSupplier`, `metricCLSID`, y `metricName` aplicaciones auxiliares también se definen en dbgmetric.h.  
  
 Un proveedor de puerto puede proporcionar su nombre y GUID a través de los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)