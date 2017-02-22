---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "Interfaz IDebugDocumentTextEvents2"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se utiliza para notificar a Visual Studio sobre los cambios en el documento de origen proporcionados por el motor de depuración.  
  
## Sintaxis  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para admitir realizar cambios en el código fuente.  Esta interfaz se implementa normalmente en el mismo objeto que implementa la interfaz de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## Notas para los llamadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obtiene esta interfaz con una llamada al método de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> .  La interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> se obtiene de una llamada al método de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> .  La interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> se obtiene llamando al método de [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugDocumentTextEvents2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que se ha destruido todo el documento.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al paquete de depuración que el texto se ha insertado en el documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al paquete de depuración que el texto se ha quitado del documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al paquete de depuración que el texto se ha reemplazado en el documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al paquete de depuración que los atributos de texto se han actualizado en el documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al receptor de eventos que se han actualizado los atributos del documento.|  
  
## Comentarios  
 Depurar sólo los motores que proporcionan sus propios documentos se aprovecharían de la interfaz de `IDebugDocumentTextEvent2` .  Un ejemplo de esto sería un motor de depuración del script.  Actual de interpretación de scripts, el nuevo código fuente puede ser generado que no está presente en ningún archivo de disco y sólo se conoce el OF.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)