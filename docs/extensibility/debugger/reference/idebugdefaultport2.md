---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f371eb040ae2c160582093f07eacb2108bcb7b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930588"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Esta interfaz proporciona varios métodos para acceder al servidor de un puerto y las facilidades de notificación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz para representar el puerto de depuración para tener acceso a programas. Un proveedor de puerto personalizado también puede implementar esta interfaz si controla la depuración remota.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un argumento a los métodos en el [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaz proporciona esta interfaz. Una llamada a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz también puede obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos definidos en [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtiene la interfaz de notificación de puerto de este puerto.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtiene la interfaz para el servidor que aloja este puerto.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina si este puerto se está ejecutando en el equipo local.|  
  
## <a name="remarks"></a>Comentarios  
 El nombre "`IDebugDefaultPort2`" es un poco de inapropiada, ya no representa un puerto predeterminado. Podría denominarse "IDebugPort3."  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)