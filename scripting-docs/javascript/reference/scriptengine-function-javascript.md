---
title: "ScriptEngine (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "ScriptEngine"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngine (función)"
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ScriptEngine (Funci&#243;n de JavaScript)
Obtiene el nombre del lenguaje de scripting en uso.  
  
## Sintaxis  
  
```  
ScriptEngine()  
```  
  
## Comentarios  
 La función `ScriptEngine` devuelve "JScript", lo que indica que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es el motor de scripting actual.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngine`:  
  
```javascript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [ScriptEngineBuildVersion \(Función\)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion \(Función\)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion \(Función\)](../../javascript/reference/scriptengineminorversion-function-javascript.md)