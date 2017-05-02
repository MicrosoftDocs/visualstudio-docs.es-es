---
title: "Recursividad (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "funciones, llamadas a funciones recursivas"
  - "procedimientos recursivos"
  - "llamadas a funciones, recursivas"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Recursividad (JavaScript)
La recursión es una técnica de programación importante en que una función se llama a sí misma.  
  
## Ejemplo de recursión  
 Un ejemplo útil de ello es el cálculo de números factoriales.  El factorial de un número *n* se calcula multiplicando 1 \* 2 \* 3 \*...  *n*.  En el ejemplo siguiente se muestra cómo calcular factoriales de forma iterativa, es decir, utilizando un bucle `while` en el que se calcula el resultado.  
  
```javascript  
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
  
 Puedes hacer que el ejemplo sea recursivo de forma muy simple.  En lugar de utilizar un bucle `while` para calcular el valor, puedes simplemente llamar a `factorial` de nuevo, pasando el valor inferior siguiente.  La recursión se detiene cuando el valor es 1.  
  
```javascript  
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