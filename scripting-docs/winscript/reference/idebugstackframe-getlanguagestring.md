---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
Devuelve una corta o una descripción textual larga del lenguaje.  
  
## Sintaxis  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### Parámetros  
 `fLong`  
 \[in\] marca, donde `TRUE` devuelve una descripción larga y `FALSE` devuelve una descripción breve.  
  
 `pbstrLanguage`  
 \[out\] descripción del lenguaje.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Normalmente, si `fLong` es `FALSE`, este método sólo proporciona el nombre del idioma asociado al marco de pila.  Cuando `fLong` es `TRUE`, este método puede proporcionar una descripción del producto completa.  
  
## Vea también  
 [IDebugStackFrame \(Interfaz\)](../../winscript/reference/idebugstackframe-interface.md)