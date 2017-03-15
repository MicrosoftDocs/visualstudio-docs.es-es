---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "Interfaz IDebugProperty3"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona compatibilidad para:  
  
-   Recupera una cadena más larga asociado a la propiedad.  
  
-   Asociar un identificador único a la propiedad.  
  
-   recuperar una lista de visores personalizados para la propiedad.  
  
-   Establecer el valor de una propiedad con la capacidad de notificar cualquier error resultantes  
  
## Sintaxis  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz en el mismo objeto que implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para proporcionar compatibilidad con cadenas largas, los id. de la propiedad, y los visores personalizados.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProperty2` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 Además de los métodos heredados de `IDebugProperty2`, la interfaz `IDebugProperty3` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Devuelve la longitud de la cadena asociada a la propiedad.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Devuelve la cadena en un búfer proporcionado por usuario.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|crea un identificador único para esta propiedad.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|destruye el identificador único para esta propiedad.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Devuelve el número de visores personalizados que esta propiedad se puede ver con.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|devuelve la lista de visores personalizados que esta propiedad se puede ver con.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Establece el valor de esta propiedad, devuelve un mensaje de error si fue mal nada.|  
  
## Comentarios  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) es la manera preferida para que el administrador de depuración de sesión \(SDM\) establezca un valor de propiedad.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)