---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
Devuelve el contexto del documento asociado a este contexto de código.  
  
## Sintaxis  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parámetros  
 `ppsc`  
 \[out\] contexto de documento de El asociado a este contexto de código.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Para los documentos de texto, el intervalo de la posición de caracteres debe incluir el texto del fragmento completo.  Esto permite al depurador el IDE resalte el fragmento actual de origen.  
  
## Vea también  
 [IDebugCodeContext \(Interfaz\)](../../winscript/reference/idebugcodecontext-interface.md)