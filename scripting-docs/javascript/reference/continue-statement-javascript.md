---
title: Continue (instrucción) (JavaScript) | Documentos de Microsoft
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
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636385"
---
# <a name="continue-statement-javascript"></a>continue (Instrucción de JavaScript)
Detiene la iteración actual de un bucle e inicia una nueva iteración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional `label` especifica el argumento de la instrucción a la que `continue` se aplica.  
  
 Puede usar el `continue` instrucción solo en un `while`, `do...while`, **para**, o `for...in` bucle. Ejecutar el `continue` instrucción se detiene la iteración actual del bucle y continúa el flujo del programa con el principio del bucle. Esto tiene los efectos siguientes en los distintos tipos de bucles:  
  
-   `while`y `do...while` bucles comprueban su condición y, si es true, vuelven a ejecutar el bucle.  
  
-   `for`bucles ejecutan su expresión de incremento y, si es true, la expresión de prueba vuelven a ejecutan el bucle.  
  
-   `for...in`bucles continúan con el siguiente campo de la variable especificada y vuelven a ejecutan el bucle.  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo, un bucle itera de 1 a 9. Las instrucciones situadas entre `continue` y el final de la `for` cuerpo se omiten debido al uso de la `continue` instrucción junto con la expresión `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 En el código siguiente, la `continue` instrucción hace referencia a la `for` bucle que va precedido por el `Inner:` etiqueta. Cuando `j` es 24, el `continue` instrucción hace que `for` bucle para ir a la siguiente iteración. Imprimirán los números de 21 a 23 y 25 a 30 en cada línea.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Instrucción while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [for... en instrucción](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)   
 [while (Instrucción)](../../javascript/reference/while-statement-javascript.md)