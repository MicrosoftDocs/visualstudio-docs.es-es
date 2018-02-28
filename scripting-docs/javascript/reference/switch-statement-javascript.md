---
title: "switch (instrucción) (JavaScript) | Documentos de Microsoft"
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
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>switch (Instrucción de JavaScript)
Habilita la ejecución de una o varias instrucciones cuando el valor de una expresión especificada coincide con una etiqueta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Parámetros  
 `expression`  
 La expresión que se debe evaluar.  
  
 `label`  
 Un identificador que debe coincidir con `expression`. Si `label` es un `expression`, inicia la ejecución con el `statementlist` inmediatamente después de los dos puntos y continúa hasta que encuentra en un `break` instrucción, que es opcional, o al final de la `switch` instrucción.  
  
 `statementlist`  
 Instrucción o instrucciones que se van a ejecutar.  
  
## <a name="remarks"></a>Comentarios  
 Use la `default` cláusula para proporcionar una instrucción que se ejecuta si ninguna de la etiqueta coincide con los valores `expression`. Puede aparecer en cualquier lugar dentro de la `switch` bloque de código.  
  
 Cero o más `label` se pueden especificar bloques. Si no hay ningún `label` coincide con el valor de `expression`y un `default` caso no se proporciona, se ejecuta ninguna instrucción.  
  
 Ejecución fluye a través de un `switch` instrucción como se indica a continuación:  
  
-   Evaluar `expression` y mire `label` en orden hasta que se encuentra una coincidencia.  
  
-   Si un `label` valor es igual a `expression`, ejecute su que acompaña a `statementlist`.  
  
     Continuar la ejecución hasta que un `break` se encuentra la instrucción, o la `switch` instrucción finaliza. Esto significa que varios `label` los bloques se ejecutan si un `break` no se utiliza la instrucción.  
  
-   Si no hay ningún `label` es igual a `expression`, vaya a la `default` caso. Si no hay ningún `default` caso, vaya al último paso.  
  
-   La ejecución continúa en la instrucción siguiente al final de la `switch` bloque de código.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se comprueba el tipo de un objeto.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>Ejemplo  
 El siguiente código muestra lo que sucede si no usa un `break` instrucción.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [if...else (Instrucción)](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)