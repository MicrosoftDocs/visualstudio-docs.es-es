---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d9c3f8b45affd192d4109db08454345dcd0814
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999727"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona puertos para el Administrador de depuración de la sesión (SDM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para representar un proveedor de puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a `CoCreateInstance` con un proveedor de puerto `GUID` devuelve esta interfaz (Esto es la forma habitual para obtener esta interfaz). Por ejemplo:  
  
```cpp#  
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
  
 Una llamada a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor del puerto actual, usando [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) devuelve esta interfaz, que representa el proveedor del puerto que se creó el puerto.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa una lista de `IDebugPortSupplier` interfaces (el `IEnumDebugPortSuppliers` interfaz se obtiene desde [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa todos los proveedores de puertos registrados con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]).  
  
 Normalmente, un motor de depuración no interactúa con un proveedor de puerto.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugPortSupplier2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtiene el nombre del proveedor de puerto.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtiene el identificador de proveedor del puerto.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtiene un puerto de un proveedor de puerto.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera los puertos que ya existen.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Comprueba que un proveedor del puerto admite la adición de nuevos puertos.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Agrega un puerto.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Quita un puerto.|  
  
## <a name="remarks"></a>Comentarios  
 Un proveedor de puerto puede identificarse por el nombre y el identificador, agregar y quitar los puertos y enumerar todos los puertos que proporciona el proveedor del puerto.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
