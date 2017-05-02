---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateTextAttributes"
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateTextAttributes
Indica que los atributos de texto asociados al intervalo subyacente de la posición de caracteres han cambiado.  
  
## Sintaxis  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### Parámetros  
 `cCharacterPosition`  
 \[in\] posición de caracteres del primer carácter que los atributos han cambiado.  
  
 `cNumToUpdate`  
 \[in\] número de caracteres del intervalo.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método indica que los atributos de texto asociados al intervalo subyacente de la posición de caracteres han cambiado.  
  
## Vea también  
 [IDebugDocumentTextEvents \(Interfaz\)](../../winscript/reference/idebugdocumenttextevents-interface.md)