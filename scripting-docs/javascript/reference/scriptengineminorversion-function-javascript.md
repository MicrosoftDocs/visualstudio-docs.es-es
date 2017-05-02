---
title: "ScriptEngineMinorVersion (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion (función)"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMinorVersion (Funci&#243;n de JavaScript)
Obtiene el número de versión secundaria del motor de scripting en uso.  
  
## Sintaxis  
  
```  
ScriptEngineMinorVersion()  
```  
  
## Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos \(DLL\) para el lenguaje de scripting en uso.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineMinorVersion`.  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [ScriptEngine \(Función\)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion \(Función\)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion \(Función\)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)