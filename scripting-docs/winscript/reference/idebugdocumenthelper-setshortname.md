---
title: "IDebugDocumentHelper::SetShortName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetShortName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetShortName"
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetShortName
Establece el nombre corto del documento.  
  
## Sintaxis  
  
```  
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### Parámetros  
 `pszShortName`  
 \[in\] cadena terminada en null que contiene el nombre corto del documento.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método establece un nuevo nombre corto del documento.  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)