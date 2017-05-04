---
title: "Errores de sintaxis de JavaScript | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "errores [JavaScript]"
  - "errores de sintaxis de JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Errores de sintaxis de JavaScript
Los errores de sintaxis de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se producen cuando la estructura de una de las instrucciones de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] infringe una o varias reglas sintácticas.  
  
## Errores  
  
|Número de error|Descripción|  
|---------------------|-----------------|  
|1019|[No puede haber 'break' fuera de un bucle](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[No puede haber 'continue' fuera de un bucle](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[La compilación condicional está desactivada](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|[La instrucción 'default' solo puede aparecer una vez en una instrucción 'switch'](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Se esperaba '\('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Se esperaba '\)'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Se esperaba '\/'](../../javascript/misc/expected-minus.md)|  
|1003|[Se esperaba ':'](../../javascript/misc/expected-colon.md)|  
|1004|[Se esperaba ';'](../../javascript/misc/expected-semicolon.md)|  
|1032|[Se esperaba '@'](../../javascript/misc/expected-at.md)|  
|1029|[Se esperaba '@end'](../../javascript/misc/expected-at-end.md)|  
|1007|[Se esperaba '&#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Se esperaba '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Se esperaba '}'](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Se esperaba '\='](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[Se esperaba 'catch'](../../javascript/misc/expected-catch.md)|  
|1031|[Se esperaba una constante](../../javascript/misc/expected-constant.md)|  
|1023|[Se esperaba un dígito hexadecimal](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Se esperaba un identificador](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Se esperaba un identificador, una cadena o un número](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Se esperaba 'while '](../../javascript/misc/expected-while.md)|  
|1014|[Carácter no válido](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[No se encuentra la etiqueta.](../../javascript/misc/label-not-found.md)|  
|1025|[Ya se definió la etiqueta](../../javascript/misc/label-redefined.md)|  
|1018|[La instrucción 'return' está fuera de una función](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Error de sintaxis](../../javascript/misc/syntax-error-javascript.md)|  
|1035|['throw' debe ir seguido de una expresión en la misma línea de código fuente](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Comentario sin terminar](../../javascript/misc/unterminated-comment.md)|  
|1015|[Constante de cadena sin terminar](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### Errores del host de script  
 Los siguientes son errores propiamente dichos del host de script, pero puede que ocurran de vez en cuando.  
  
|Error|HRESULT|Descripción|  
|-----------|-------------|-----------------|  
|SCRIPT\_E\_RECORDED|0x86664004|Se ha registrado un error pasado entre el motor y el host de script.  El host tiene que pasar el código de error al llamador.|  
|SCRIPT\_E\_REPORTED|0x80020101|El motor de script ha notificado una excepción no controlada al host con IActiveScriptSite::OnScriptError.  El host puede hacer caso omiso de este error.|  
|SCRIPT\_E\_PROPAGATE|0x8002010|Se está propagando un error de script al llamador que podría estar en un subproceso diferente.  El host debe pasar el código de error al llamador.|  
  
## Vea también  
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)