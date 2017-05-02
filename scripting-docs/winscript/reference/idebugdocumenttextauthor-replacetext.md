---
title: "IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::ReplaceText"
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::ReplaceText
Reemplaza el texto en el documento.  
  
## Sintaxis  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### Parámetros  
 `cCharacterPosition`  
 \[in\] ubicación de inicio del intervalo de caracteres a reemplazar.  
  
 `cNumToReplace`  
 \[in\] número de caracteres que se va a reemplazar.  
  
 `pcharText[]`  
 \[in\] búfer de que contiene los caracteres nuevos para reemplazar los antiguos caracteres.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método reemplaza el texto en el documento.  
  
## Vea también  
 [IDebugDocumentTextAuthor \(Interfaz\)](../../winscript/reference/idebugdocumenttextauthor-interface.md)