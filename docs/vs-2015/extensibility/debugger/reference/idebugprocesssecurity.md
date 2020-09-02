---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 836b971963587aa89440c6e023ee255612d2a087
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187942"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` lo implementa un proveedor de puerto para advertir al usuario de que la asociación al proceso no es segura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugProcessSecurity` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario del proveedor del puerto.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte que un usuario que se asocia al proceso de depuración no es seguro.|  
  
## <a name="remarks"></a>Comentarios  
 Implemente esta interfaz para mostrar una advertencia y permitir que el usuario cancele si el proceso al que se va a adjuntar se puede considerar no seguro.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Puerto](../../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
