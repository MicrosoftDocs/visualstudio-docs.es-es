---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
Notifica al host que se está creando un contexto de nuevo documento y permite al host devuelve opcionalmente un desconocido que controla para el nuevo contexto.  
  
## Sintaxis  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### Parámetros  
 `ppunkOuter`  
 \[out\] objeto que controla el nuevo contexto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no proporciona un objeto que controla.|  
  
## Comentarios  
 Este método permite al host agregue nueva funcionalidad a aplicación auxiliar\- proporcionaba contextos de documento.  Este método puede devolver **E\_NOTIMPL** o un objeto externo null, en cuyo caso el llamador es responsable de crear el contexto.  
  
## Vea también  
 [IDebugDocumentHost \(Interfaz\)](../../winscript/reference/idebugdocumenthost-interface.md)