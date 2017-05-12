---
title: "ScriptEngineMajorVersion (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion (función)"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMajorVersion (Funci&#243;n de JavaScript)
Obtiene el número de versión principal del motor de scripting en uso.  
  
## Sintaxis  
  
```  
ScriptEngineMajorVersion()  
```  
  
## Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos \(DLL\) para el lenguaje de scripting en uso.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineMajorVersion`:  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [ScriptEngine \(Función\)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion \(Función\)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion \(Función\)](../../javascript/reference/scriptengineminorversion-function-javascript.md)