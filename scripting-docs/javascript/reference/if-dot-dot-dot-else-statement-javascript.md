---
title: If... else (instrucción) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637335"
---
# <a name="ifelse-statement-javascript"></a>if...else (Instrucción de JavaScript)
Ejecuta condicionalmente un grupo de instrucciones en función del valor de una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Parámetros  
 `condition1`  
 Obligatorio. Expresión booleana. Si `condition1` es `null` o `undefined`, `condition1` se trata como `false`.  
  
 `statement1`  
 Opcional. La instrucción que se ejecutará si `condition1` es **true**. Puede ser una instrucción compuesta.  
  
 `condition2`  
 La condición que se va a evaluar.  
  
 `statement2`  
 Opcional. La instrucción que se ejecutará si `condition2` es `true`. Puede ser una instrucción compuesta.  
  
 `statement3`  
 Si ambos `condition1` y `condition2` son `false`, se ejecuta esta instrucción.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar `if`, `if else`, y `else`.  
  
 Es recomendable que se encierra `statement1` y `statement2` entre llaves ({}) para mayor claridad y para evitar errores involuntarios.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador condicional ternario (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)