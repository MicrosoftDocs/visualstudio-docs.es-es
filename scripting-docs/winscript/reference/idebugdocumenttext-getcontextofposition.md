---
title: "IDebugDocumentText::GetContextOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetContextOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetContextOfPosition"
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetContextOfPosition
Crea un objeto de contexto del documento correspondiente al intervalo proporcionado de la posición.  
  
## Sintaxis  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parámetros  
 `cCharacterPosition`  
 \[in\] ubicación de inicio del intervalo de la posición.  
  
 `cNumChars`  
 \[in\] número de caracteres del intervalo.  
  
 `ppsc`  
 \[out\] objeto de contexto del documento de El correspondiente al intervalo especificado de la posición.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea un objeto de contexto del documento correspondiente al intervalo proporcionado de la posición.  
  
## Vea también  
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)