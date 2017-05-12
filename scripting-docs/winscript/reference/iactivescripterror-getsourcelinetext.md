---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
Recupera la línea del archivo de código fuente donde un error mientras que un motor de script ejecuta un script.  
  
## Sintaxis  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Parámetro  
 `pbstrSourceLine`  
 \[out\] dirección de un búfer que recibe la línea de código fuente en la que se produjo el error.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL` si la línea del archivo de código fuente no se recuperará.  
  
## Vea también  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)