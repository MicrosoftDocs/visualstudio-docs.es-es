---
title: "IDebugDocumentHelper::AddUnicodeText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddUnicodeText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddUnicodeText"
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddUnicodeText
Anexa una cadena Unicode al final de este documento.  
  
## Sintaxis  
  
```  
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### Parámetros  
 `pszText`  
 \[in\] puntero a una cadena terminada en null que contiene el texto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no pudo agregar caracteres.|  
  
## Comentarios  
 Este método genera las notificaciones de `IDebugDocumentTextEvents` .  
  
> [!NOTE]
>  Si se llama a este método después de llamar a `AddDeferredText` , se devuelve `E_FAIL` .  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents \(Interfaz\)](../../winscript/reference/idebugdocumenttextevents-interface.md)