---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
Devuelve el conjunto de caracteres de finalizaciones para un contexto solicitado de finalización.  
  
## Sintaxis  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### Parámetros  
 `fRequestedList`  
 \[in\] contexto solicitado The de finalización.  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|Solicita la enumeración del lado izquierdo.|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|Solicita el contexto del miembro.|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|Solicita la lista de parámetros.|  
|SCRIPT\_CMPL\_COMMIT|0x0004|Solicita la finalización de la lista de parámetros.|  
  
 `pbstrChars`  
 \[out\] caracteres a El que corresponden al contexto solicitado de finalización.  
  
|Parámetro `fRequestedList`|Caracteres devueltos|  
|--------------------------------|--------------------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|“\=”|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|“\(,”|  
|SCRIPT\_CMPL\_COMMIT|“\(\)”|  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)