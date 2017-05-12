---
title: "@set (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set (instrucción)"
  - "compilación condicional, variables"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# @set (Instrucci&#243;n de JavaScript)
Crea variables utilizadas con instrucciones de compilación condicional.  
  
> [!WARNING]
>  La compilación condicional no se admite en el modo estándar de Internet Explorer 11 ni en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  En cambio, sí se admite en el modo estándar de Internet Explorer 10 y en las versiones anteriores.  
  
## Sintaxis  
  
```  
  
@set @varname = term   
```  
  
## Parámetros  
 *varname*  
 Obligatorio.  Nombre de variable de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido.  Debe ir siempre precedido de un carácter "@".  
  
 `term`  
 Obligatorio.  Cero o más operadores unarios seguidos de una constante, variable de compilación condicional o expresión entre paréntesis.  
  
## Comentarios  
 Las variables de tipo numérico y booleano se admiten en la compilación condicional.  Las variables de cadena no se aceptan.  Las variables creadas mediante `@set` se suelen usar en instrucciones de compilación condicional, aunque se pueden usar en cualquier parte del código de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Los ejemplos de declaraciones de variable tienen este aspecto:  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 En las expresiones entre paréntesis se admiten los siguientes operadores:  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Si una variable se usa antes de que se defina, su valor es `NaN`.  `NaN` se puede comprobar mediante la instrucción `@if`:  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Esto es posible porque `NaN` es el único valor que no es igual a sí mismo.  
  
## Requisitos  
 Se admite en todas las versiones de Internet Explorer, pero no en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on \(Instrucción\)](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if \(Instrucción\)](../../javascript/reference/at-if-statement-javascript.md)