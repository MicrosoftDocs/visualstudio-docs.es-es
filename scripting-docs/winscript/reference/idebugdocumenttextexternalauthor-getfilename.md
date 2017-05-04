---
title: "IDebugDocumentTextExternalAuthor::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetFileName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetFileName"
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetFileName
Devuelve el nombre del documento sin información de ruta de acceso.  
  
## Sintaxis  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### Parámetros  
 `pbstrShortName`  
 \[out\] vinculadas contener el nombre corto del documento.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el nombre del documento sin información de ruta de acceso.  El nombre corto se usa normalmente en cuadros de diálogo.  
  
## Vea también  
 [IDebugDocumentTextExternalAuthor \(Interfaz\)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)