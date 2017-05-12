---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
Devuelve el nombre del documento especificado.  
  
## Sintaxis  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### Parámetros  
 `dnt`  
 \[in\] tipo de nombre del documento a devolver.  
  
 `pbstrName`  
 \[out\] una cadena que contiene el nombre.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El nombre del documento especificado no se conoce.|  
  
## Comentarios  
 Este método devuelve el nombre del documento especificado.  
  
## Vea también  
 [IDebugDocumentInfo \(Interfaz\)](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE \(Enumeración\)](../../winscript/reference/documentnametype-enumeration.md)