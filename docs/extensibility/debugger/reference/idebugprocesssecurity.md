---
title: IDebugProcessSecurity | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7acdb0f16182ebca904229d7620b80f5ec81d1de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`se implementa mediante un proveedor de puerto para advertir al usuario que no es seguro asociarse al proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProcessSecurity`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario desde el proveedor del puerto.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte al usuario que asociar al proceso de depuración no es seguro.|  
  
## <a name="remarks"></a>Comentarios  
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario pueda cancelar si el proceso al que desea adjuntar puede considerarse no seguro.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)