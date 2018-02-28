---
title: Errores de sintaxis de JavaScript | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>Errores de sintaxis de JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]errores de sintaxis se producen cuando la estructura de uno de sus [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instrucciones infringe una o varias de las reglas sintácticas.  
  
## <a name="errors"></a>Errores  
  
|Número de error|Descripción|  
|------------------|-----------------|  
|1019|["break" no puede estar fuera del bucle](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|["continue" no puede estar fuera del bucle](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[La compilación condicional está desactivada](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|["default" solo puede aparecer una vez en una instrucción "switch"](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Se esperaba ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Se esperaba ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Se esperaba '/'](../../javascript/misc/expected-minus.md)|  
|1003|[Se esperaba ":"](../../javascript/misc/expected-colon.md)|  
|1004|[Se esperaba ";"](../../javascript/misc/expected-semicolon.md)|  
|1032|[Se esperaba "@"](../../javascript/misc/expected-at.md)|  
|1029|[Se esperaba "@end"](../../javascript/misc/expected-at-end.md)|  
|1007|[Se esperaba ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Se esperaba "{"](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Se esperaba "}"](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Se esperaba '='](../../javascript/misc/expected-equal-javascript.md)|  
|3082|[Se esperaba "catch"](../../javascript/misc/expected-catch.md)|  
|1031|[Se esperaba una constante](../../javascript/misc/expected-constant.md)|  
|1023|[Se esperaba un dígito hexadecimal](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Se esperaba un identificador](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Se esperaba un identificador, una cadena o un número](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Se esperaba "while"](../../javascript/misc/expected-while.md)|  
|1014|[Carácter no válido](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[No se encuentra la etiqueta](../../javascript/misc/label-not-found.md)|  
|1025|[Etiqueta redefinida](../../javascript/misc/label-redefined.md)|  
|1018|[instrucción "return" fuera de función](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Error de sintaxis](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Throw debe ir seguido de una expresión en la misma línea de código fuente](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Comentario sin terminar](../../javascript/misc/unterminated-comment.md)|  
|1015|[Constante de cadena sin terminar](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Errores de Host de script  
 Los siguientes errores correctamente hablar errores relacionados con el host de script, pero puede verlos en ocasiones.  
  
|Error|HRESULT|Descripción|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Se ha registrado un error para pasar entre el host y el motor de scripts. El host debe pasar el código de error al llamador.|  
|SCRIPT_E_REPORTED|0 x 80020101|Motor de secuencia de comandos ha informado de una excepción no controlada al host a través de IActiveScriptSite::OnScriptError. Host puede omitir este error.|  
|SCRIPT_E_PROPAGATE|0x8002010|Un error de script se propaga al llamador que podría estar en un subproceso diferente. El host debe pasar el código de error al llamador.|  
  
## <a name="see-also"></a>Vea también  
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)