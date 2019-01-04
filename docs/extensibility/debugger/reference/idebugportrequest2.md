---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a05f84d685ac33203461dfc1b0f515cb45f67c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876934"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Esta interfaz describe un puerto. Esta descripción se utiliza para agregar el puerto a un proveedor de puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio normalmente implementa esta interfaz en el proceso de obtención de un puerto de depuración de un proveedor de puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se pasa a [agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para crear un puerto de depuración. Una llamada a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) devuelve esta interfaz, que representa la solicitud utilizada para crear el puerto en primer lugar.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugPortRequest2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtiene el nombre del puerto que se va a crear.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, un motor de depuración no interactúa con un proveedor de puerto y no tendrá ningún uso para esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)