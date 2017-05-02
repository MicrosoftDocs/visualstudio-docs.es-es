---
title: "IDebugDocumentHost::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetPathName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetPathName"
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetPathName
Devuelve la ruta de acceso completa y el nombre del archivo de código fuente del documento.  
  
## Sintaxis  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Parámetros  
 `pbstrLongName`  
 \[out\] cadena de que contiene el nombre largo de archivo.  
  
 `pfIsOriginalFile`  
 \[out\] A marcadores que es true si `pbstrLongName` hace referencia al archivo original del documento, false.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Ningún archivo de código fuente puede crear o determinar.|  
  
## Comentarios  
 Este método devuelve la ruta de acceso completa y el nombre del archivo de código fuente del documento.  
  
## Vea también  
 [IDebugDocumentHost \(Interfaz\)](../../winscript/reference/idebugdocumenthost-interface.md)