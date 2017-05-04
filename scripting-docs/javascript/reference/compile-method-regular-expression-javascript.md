---
title: "compile (M&#233;todo, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile (método)"
  - "compilar código fuente, expresiones regulares"
  - "expresiones regulares, compilar"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile (M&#233;todo, Regular Expression de JavaScript)
Compila una expresión regular y la convierte a un formato interno para una ejecución más rápida.  
  
## Sintaxis  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## Parámetros  
 `rgExp`  
 Obligatorio.  Instancia de un objeto **Regular Expression**.  Puede ser un nombre de variable o un literal.  
  
 *pattern*  
 Obligatorio.  Expresión de cadena que contiene un patrón de expresión regular que se va a compilar.  
  
 `flags`  
 Opcional.  Las marcas disponibles, que se pueden combinar, son:  
  
-   g \(búsqueda global de todas las repeticiones de *pattern*\)  
  
-   i \(pasar por alto mayúsculas y minúsculas\)  
  
-   m \(búsqueda en varias líneas\)  
  
## Comentarios  
 El método **compile** convierte el argumento *pattern* a un formato interno para que la ejecución sea más rápida.  Esto permite un uso más eficiente de las expresiones regulares en bucles, por ejemplo.  Una expresión regular compilada aumenta la velocidad cuando se reutiliza la misma expresión repetidamente.  Sin embargo, no se obtiene ninguna ventaja si la expresión regular cambia.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **compile**:  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)