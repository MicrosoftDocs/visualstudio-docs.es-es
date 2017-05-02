---
title: "ScriptEngineBuildVersion (Funci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion (función)"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ScriptEngineBuildVersion (Funci&#243;n de JavaScript)
Obtiene el número de versión de compilación del motor de scripting en uso.  
  
## Sintaxis  
  
```  
ScriptEngineBuildVersion()  
```  
  
## Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos \(DLL\) para el lenguaje de scripting en uso.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineBuildVersion`:  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [ScriptEngine \(Función\)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion \(Función\)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion \(Función\)](../../javascript/reference/scriptengineminorversion-function-javascript.md)