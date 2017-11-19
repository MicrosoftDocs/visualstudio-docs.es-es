---
title: "para la instrucción (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>for (Instrucción de JavaScript)
Ejecuta un bloque de instrucciones mientras una condición especificada sea true.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Parámetros  
 `initialization`  
 Opcional. Una expresión. Esta expresión se ejecuta sólo una vez, antes de que se ejecuta el bucle.  
  
 `test`  
 Opcional. Expresión booleana. Si `test` es `true`, `statement` se ejecuta. Si `test` si `false`, se termina el bucle.  
  
 `increment`  
 Opcional. Una expresión. La expresión de incremento se ejecuta al final de cada paso del bucle.  
  
 `statement`  
 Opcional. Una o más instrucciones que se ejecutarán si `test` es **true**. Puede ser una instrucción compuesta.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente se utiliza un `for` bucle cuando se ejecuta un número de veces que el bucle. Un `for` bucle es útil para recorrer en iteración matrices y para realizar el procesamiento secuencial.  
  
 La prueba de una expresión condicional se produce antes de la ejecución del bucle, por lo que un `for` instrucción ejecuta cero o más veces.  
  
 En cualquier línea de un `for` bloque de instrucciones de bucle, puede utilizar el `break` instrucción para salir del bucle, o se puede utilizar el `continue` instrucción para transferir el control a la siguiente iteración del bucle.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la `for` instrucción ejecuta las instrucciones entre paréntesis, como se indica a continuación:  
  
-   Primero, el valor inicial de la variable `i` se evalúa.  
  
-   A continuación, siempre que el valor de `i` es menor o igual a 9, la `document.write` se ejecutan las instrucciones y `i` se vuelve a evaluar.  
  
-   Cuando `i` es mayor que 9, la condición es false y el control se transfiere fuera del bucle.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Ejemplo  
 Todas las expresiones de la `for` instrucción son opcionales. En el ejemplo siguiente, la `for` instrucciones crean un bucle infinito y un `break` instrucción se utiliza para salir del bucle.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [for... en instrucción](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while (Instrucción)](../../javascript/reference/while-statement-javascript.md)