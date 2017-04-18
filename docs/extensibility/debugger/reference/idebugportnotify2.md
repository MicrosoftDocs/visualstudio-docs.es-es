---
title: IDebugPortNotify2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: de163fdf55052ff4cc2f1599bc8ddfd162d03df3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Esta interfaz se registra o se anula el registro de un programa que se puede depurar con el puerto que se ejecuta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para admitir agregar y quitar programas del puerto. Normalmente se implementa en el mismo objeto que implementa el [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [QueryInterface](/cpp/atl/queryinterface) en el `IDebugPort2` interfaz devuelve esta interfaz. Además, una llamada a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) devuelve esta interfaz. Un motor de depuración puede ver esta interfaz como un parámetro a [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugPortNotify2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programa que se puede depurar con el puerto que se ejecuta.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Anula el registro de un programa que se puede depurar en el puerto que se ejecuta.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que un puerto de depuración tiene una manera de saber cuándo se cargan o descargan los programas, un proveedor de puerto personalizado debe implementar esta interfaz. Todos los programas que se cargan para la depuración a través de un puerto determinado se realiza el seguimiento de uso de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
