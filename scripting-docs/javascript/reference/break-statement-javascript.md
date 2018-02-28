---
title: "break (instrucción) (JavaScript) | Documentos de Microsoft"
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
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>break (Instrucción de JavaScript)
Finaliza el bucle actual o si junto con un `label`, finaliza la instrucción asociada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional `label` argumento especifica la etiqueta de la instrucción que se desea interrumpir.  
  
 Normalmente, se utiliza el `break` instrucción `switch` instrucciones y en `while`, `for`, `for...in`, o `do...while` bucles. Se suele utilizar el `label` argumento en `switch` instrucciones, pero puede usarse en cualquier instrucción, ya sea simple o compuesta.  
  
 Ejecutar el `break` instrucción sale de la instrucción o bucle actual y comienza la ejecución de secuencias de comandos con la instrucción inmediatamente posterior.  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo, el contador está configurado para contar de 1 a 99; Sin embargo, la `break` instrucción termina el bucle tras 14 recuentos.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 En el código siguiente, la `break` instrucción hace referencia a la `for` bucle que va precedido por el `Inner:` instrucción. Cuando `j` es igual a 24, la `break` instrucción hace que el flujo del programa salir del bucle. Los números 21 al 23 de impresión en cada línea.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Continue (instrucción)](../../javascript/reference/continue-statement-javascript.md)   
 [Instrucción while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [for... en instrucción](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)   
 [while (Instrucción)](../../javascript/reference/while-statement-javascript.md)