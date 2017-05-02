---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetPathName"
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetPathName
Devuelve la ruta de acceso completa y el nombre de archivo del documento.  
  
## Sintaxis  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Parámetros  
 `pbstrLongName`  
 \[out\] vinculadas contener la ruta de acceso completa y el nombre de archivo.  
  
 `pfIsOriginalFile`  
 \[out\] booleano que indica si la ruta de acceso y nombre de archivo hacen referencia al documento original.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El archivo de código fuente no pueden crearse o determinar.|  
  
## Comentarios  
 Este método devuelve la ruta de acceso completa y el nombre de archivo del documento.  
  
 Si `pfIsOriginalFile` es FALSE, la ruta de acceso y nombre de archivo en `pbstrLongName` hacen referencia a un archivo temporal creado recientemente.  
  
## Vea también  
 [IDebugDocumentTextExternalAuthor \(Interfaz\)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)