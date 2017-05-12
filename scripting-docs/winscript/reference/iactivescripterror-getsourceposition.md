---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
Recupera la ubicación en el código fuente donde se produjo un error mientras el motor de script ejecuta un script.  
  
## Sintaxis  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### Parámetros  
 `pdwSourceContext`  
 \[out\] dirección de una variable que recibe una cookie que identifica el contexto.  La interpretación de este parámetro depende de la aplicación host.  
  
 `pulLineNumber`  
 \[out\] dirección de una variable que recibe el número de línea en el archivo de código fuente donde se produjo el error.  
  
 `pichCharPosition`  
 \[out\] dirección de una variable que recibe la posición de carácter en la línea donde se produjo el error.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL` si la ubicación no se recuperará.  
  
## Vea también  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)