---
title: IDebugPortSupplier2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119479"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Esta interfaz proporciona puertos para el Administrador de sesión de depuración (SDM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para representar un proveedor del puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a `CoCreateInstance` con un proveedor de puerto `GUID` devuelve esta interfaz (es decir, la forma habitual para obtener esta interfaz). Por ejemplo:  
  
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
  
 Una llamada a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor actual del puerto que usa [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor del puerto que creó el puerto.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa una lista de `IDebugPortSupplier` interfaces (la `IEnumDebugPortSuppliers` interfaz se obtiene del [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa todos los proveedores de puerto registrado con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Un motor de depuración normalmente no interactúan con un proveedor del puerto.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugPortSupplier2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtiene el nombre de proveedor de puerto.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtiene el identificador de proveedor del puerto.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtiene un puerto de un proveedor del puerto.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera los puertos que ya existen.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Comprueba que un proveedor del puerto admite la adición de nuevos puertos.|  
|[Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Agrega un puerto.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Quita un puerto.|  
  
## <a name="remarks"></a>Comentarios  
 Un proveedor de puerto puede identificarse por nombre y el identificador, agregar y quitar los puertos y enumerar todos los puertos que proporciona el proveedor del puerto.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)