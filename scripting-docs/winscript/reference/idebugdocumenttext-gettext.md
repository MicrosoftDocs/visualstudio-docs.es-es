---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
Recupera los caracteres o los atributos de caracteres asociados a un intervalo de la posición.  
  
## Sintaxis  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parámetros  
 `cCharacterPosition`  
 \[in\] ubicación de inicio del intervalo de la posición.  
  
 `pcharText`  
 \[in, out\] búfer de texto de caracteres de A.  El búfer debe ser lo suficientemente grande para contener los caracteres de `cMaxChars` .  Si este parámetro es NULL, el método no devuelve los caracteres.  
  
 `pstaTextAttr`  
 \[in, out\] búfer de atributo de carácter de A.  El búfer debe ser lo suficientemente grande para contener los caracteres de `cMaxChars` .  Si este parámetro es NULL, el método no devuelve atributos.  
  
 `pcNumChars`  
 \[in, out\] número de caracteres de El\/atributos devueltos.  Este parámetro se debe establecer en cero antes de llamar a este método.  
  
 `cMaxChars`  
 \[in\] número de caracteres del intervalo de la posición.  También especifica el número máximo de caracteres para devolver.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera los caracteres o los atributos de caracteres asociados a una posición de caracteres van.  El intervalo de la posición del carácter especificado por una posición de caracteres y varios caracteres.  
  
## Vea también  
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)