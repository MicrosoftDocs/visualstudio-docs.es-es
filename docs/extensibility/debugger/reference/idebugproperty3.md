---
title: IDebugProperty3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3
helpviewer_keywords: IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 091ebddc0c3424bdbf8126257fe56e6959bc28c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3"></a>IDebugProperty3
Esta interfaz proporciona compatibilidad para:  
  
-   Recuperar una cadena de longitud arbitraria asociada a la propiedad.  
  
-   Asocia un identificador único a la propiedad.  
  
-   Recuperar una lista de visores personalizados para la propiedad.  
  
-   Establecer el valor de una propiedad con la posibilidad de notificar cualquier error resultante  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz en el mismo objeto que implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para proporcionar compatibilidad con cadenas largas, identificadores de propiedad y visores personalizados.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProperty2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de `IDebugProperty2`, el `IDebugProperty3` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Devuelve la longitud de la cadena asociada a la propiedad.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Devuelve la cadena en un búfer proporcionado por el usuario.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crea un identificador único para esta propiedad.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Destruye el identificador único para esta propiedad.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Devuelve el número de visores personalizados que se puede ver con esta propiedad.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Devuelve la lista de visores personalizados que se puede ver con esta propiedad.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Establece el valor de esta propiedad, devuelve un mensaje de error si todo lo produjo un error.|  
  
## <a name="remarks"></a>Comentarios  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) es la manera preferida para el Administrador de sesión de depuración (SDM) para establecer el valor de la propiedad.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)