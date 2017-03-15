---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugPropertyCreateEvent2"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es enviada por el motor de depuración \(DE\) al administrador de depuración de la sesión \(SDM\) cuando crea una propiedad que está asociado a un documento concreto.  
  
## Sintaxis  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para indicar que se ha creado una propiedad.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  Se implementa esta interfaz si el OF ha creado una propiedad asociada con un script que ha cargado o creado y si ese script debe aparecer en el IDE.  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para indicar que se ha creado una propiedad.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se asocia al programa que se depura.  
  
## métodos en el orden de Vtable  
 la tabla siguiente muestra el método de la interfaz de `IDebugPropertyCreateEvent2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|obtiene la nueva propiedad.|  
  
## Comentarios  
 Si una propiedad tiene un documento o un script asociado, el OF puede enviar este evento al SDM para actualizar la ventana de **Documentos de script** con el nombre del documento.  El SDM llamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con el argumento `guidDocument` para recuperar `VARIANT` que contiene un puntero de [IUnknown](/visual-cpp/atl/iunknown) .  El SDM llamará [QueryInterface](/visual-cpp/atl/queryinterface) en este puntero para recuperar la interfaz de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que se utiliza para actualizar la ventana de **Documentos de script** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)