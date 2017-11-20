---
title: "DO... while (instrucción de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while (Instrucción de JavaScript)
Ejecuta un bloque de instrucciones una vez y, a continuación, repite la ejecución del bucle hasta que se evalúa como una expresión de condición `false`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Parámetros  
 `statement`  
 Obligatorio. La instrucción que se ejecutará si `expression` es `true`. Puede ser una instrucción compuesta.  
  
 `expression`  
 Obligatorio. Una expresión que puede convertirse a un valor booleano `true` o `false`. Si `expression` es `true`, el bucle se ejecuta de nuevo. Si `expression` es `false`, se termina el bucle.  
  
## <a name="remarks"></a>Comentarios  
 A diferencia de la `while` (instrucción), un `do...while` bucle se ejecuta una vez antes de que se evalúa la expresión condicional.  
  
 En cualquier línea de un `do...while` bloque, puede usar el `break` instrucción para hacer que el flujo del programa salir del bucle, o se puede utilizar el `continue` instrucción para ir directamente a la `while` expresión.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, las instrucciones de la `do...while` seguir ejecutándose mientras la variable de bucle `i` es menor que 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, las instrucciones dentro del bucle se ejecutan una vez, aunque no se cumple la condición.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Continue (instrucción)](../../javascript/reference/continue-statement-javascript.md)   
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [for... en instrucción](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while (instrucción)](../../javascript/reference/while-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)