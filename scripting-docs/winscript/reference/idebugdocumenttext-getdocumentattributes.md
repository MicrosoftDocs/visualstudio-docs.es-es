---
title: "IDebugDocumentText::GetDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetDocumentAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetDocumentAttributes"
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetDocumentAttributes
Devuelve los atributos del documento.  
  
## Sintaxis  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### Parámetros  
 `ptextdocattr`  
 \[out\] atributos de texto del documento.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve los atributos del documento.  
  
## Vea también  
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [TEXT\_DOC\_ATTR \(Constantes\)](../../winscript/reference/text-doc-attr-constants.md)