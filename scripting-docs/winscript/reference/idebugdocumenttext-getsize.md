---
title: "IDebugDocumentText::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetSize"
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetSize
Devuelve el número de líneas y de número de caracteres del documento.  
  
## Sintaxis  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### Parámetros  
 `pcNumLines`  
 \[out\] número de líneas del documento.  Si este parámetro es NULL, el método no devuelve un valor.  
  
 `pcNumChars`  
 \[out\] número de caracteres del documento.  Si este parámetro es NULL, el método no devuelve un valor.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el número de líneas y de número de caracteres del documento.  
  
## Vea también  
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)