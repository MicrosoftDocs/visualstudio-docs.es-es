---
title: "IDebugDocumentTextEvents (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents (interfaz)"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents (Interfaz)
Proporciona eventos que indican cambios en el documento de texto asociado.  
  
> [!NOTE]
>  Cambia el texto del documento cuando los eventos en esta interfaz desencadenan.  Los controladores de eventos pueden recuperar el nuevo texto mediante la interfaz de `IDebugDocumentText` .  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugDocumentTextEvents` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica que se ha destruido el documento subyacente y ya no es válido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica que el nuevo texto se ha agregado al documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica que el texto se ha quitado del documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica que se ha reemplazado el texto.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica que los atributos de texto asociados al intervalo subyacente de la posición de caracteres han cambiado.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica que los atributos del documento han cambiado.|