---
title: IDebugProcessSecurity | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e34a93e73bd1c4c9b5e70f89d318c2db6a84f2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967961"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` se implementa mediante un proveedor de puerto para advertir al usuario que no es seguro asociar al proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProcessSecurity`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario desde el proveedor del puerto.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte al usuario que no es seguro asociar al proceso de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario pueda cancelar si el proceso al que va a asociar puede considerarse no seguro.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)