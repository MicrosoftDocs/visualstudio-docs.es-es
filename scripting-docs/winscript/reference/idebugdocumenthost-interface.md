---
title: "IDebugDocumentHost (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost (interfaz)"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost (Interfaz)
Expone la funcionalidad host\- específica, como colorear la sintaxis, el depurador.  El método de `IDebugDocumentHelper::SetDebugDocumentHost` realiza esta interfaz como argumento.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugDocumentHost` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Devuelve un intervalo de caracteres que se agregaron utilizando `IDebugDocumentHelper::AddDeferredText`, en el documento de host original.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de texto del documento.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Notifica al host que un contexto de nuevo documento se crea, y permite al host devuelve opcionalmente un objeto que controla el nuevo contexto.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Devuelve la ruta de acceso completa \(incluso el nombre de archivo\) del archivo de código fuente del documento.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Devuelve el nombre del documento, sin la ruta de acceso.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Notifica al host que se ha guardado el archivo de código fuente del documento y que su contenido debe actualizarse.|