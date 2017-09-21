---
title: "Implementar y registrar un proveedor de puerto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], registrar proveedores de puertos"
  - "proveedores de puertos, registrar"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Implementar y registrar un proveedor de puerto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El rol de un proveedor de puerto es los puertos seguir y de fuente, que a su vez administran procesos.  Cuando un puerto necesita crear, el proveedor de puerto se crea instancias utilizando CoCreate con el GUID del proveedor de puerto \(la sesión del administrador de depuración \[SDM\] utilizará el proveedor de puerto el usuario seleccionado o el proveedor de puerto especificado por el sistema de proyectos\).  El SDM llamará a [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver si algunos puertos pueden agregar.  Si un puerto puede agregarse, un nuevo puerto es solicitado llamando a [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) y pasando [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que describa el puerto.  `AddPort` devolverá un nuevo puerto representado por una interfaz de [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## Explicación  
 Un puerto es creado por un proveedor de puerto, que a su vez asociado a un equipo o de depuración.  Un servidor puede enumerar los proveedores de puerto con el método de[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , y un proveedor de puerto puede enumerar los puertos con el método de [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Además del registro COM típico, un proveedor de puerto debe registrarse con Visual Studio colocando el CLSID y nombre en ubicaciones específicas del registro.  Una aplicación auxiliar `SetMetric` denominado función de SDK de depuración controla esta tarea: se llama una vez para cada elemento se registre, así:  
  
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
  
 Anula el propio de un proveedor de puerto llamando a `RemoveMetric` \(otra función auxiliar de SDK de depuración\) una vez por cada elemento registrado, así:  
  
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
>  [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` y `RemoveMetric` son funciones estáticas definido en dbgmetric.h y compiladas en ad2de.lib.  `metrictypePortSupplier`, `metricCLSID`, y aplicaciones auxiliares de`metricName` también son definido en dbgmetric.h.  
  
 Un proveedor de puerto puede proporcionar un nombre y GUID a los métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) y [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## Vea también  
 [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)