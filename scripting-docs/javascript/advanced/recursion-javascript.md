---
title: Recursividad (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- functions, recursive function calls
- recursive procedures
- function calls, recursive
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06735c244ed6bd3c8d9abe59123f9f961e6f1847
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="recursion-javascript"></a>Recursividad (JavaScript)
La recursividad es una técnica de programación importante, en la que una función se llama a sí misma.  
  
## <a name="an-example-of-recursion"></a>Ejemplo de recursividad  
 Un ejemplo es el cálculo de factoriales. El factorial de un número *n* se calcula al multiplicar 1 \* 2 \* 3 \*... *n*. En el ejemplo siguiente, se muestra cómo calcular factoriales de forma iterativa, es decir, mediante un bucle `while` en el que se calcula el resultado.  
  
```JavaScript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Puede convertir el ejemplo en recursivo de un modo muy sencillo. En lugar de usar un bucle `while` para calcular el valor, puede volver a llamar a `factorial`, pasando el siguiente valor más bajo. La recursividad se detiene cuando el valor es 1.  
  
```JavaScript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```