---
title: "IDebugDocumentHelper::SetDefaultTextAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDefaultTextAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDefaultTextAttr"
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDefaultTextAttr
Establece los atributos predeterminados para utilizar para el texto que no está en un bloque de script.  
  
## Sintaxis  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### Parámetros  
 `staTextAttr`  
 Los atributos de texto predeterminadas de origen.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 A menos que los atributos predeterminados se cambien con este método, los atributos predeterminados del texto fuera de un bloque de script son SOURCETEXT\_ATTR\_NONSOURCE.  La interfaz de usuario puede usar esta información para marcar el texto fuera de los bloques de script como de sólo lectura.  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)