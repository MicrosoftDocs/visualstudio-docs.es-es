---
title: Precedencia de operadores (JavaScript) | Microsoft Docs
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
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="operator-precedence-javascript"></a>Precedencia de operadores (JavaScript)
La prioridad de operador describe el orden en que se realizan las operaciones cuando se evalúa una expresión. Las operaciones con mayor prioridad se realizan antes que las de menor prioridad. Por ejemplo, la multiplicación se realiza antes que la suma.  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>Operadores de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
 En la tabla siguiente se indican los operadores de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], ordenados de mayor a menor prioridad. Los operadores que tienen la misma prioridad se evalúan de izquierda a derecha.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|. [ ] ( )|Acceso a campos, indización de matrices, llamadas a funciones y agrupamiento de expresiones|  
|++ -- - ~ ! delete new typeof void|Operadores unarios, tipos de datos devueltos, creación de objetos, valores no definidos|  
|* / %|Multiplicación, división, división módulo|  
|+ - +|Suma, resta, concatenación de cadenas|  
|<\< >> >>>|Desplazamiento bit a bit|  
|< \<= > >= instanceof|Menor que, menor o igual que, mayor que, mayor o igual que, instanceof|  
|== != === !==|Igualdad, desigualdad, igualdad estricta y desigualdad estricta|  
|&|AND bit a bit|  
|^|XOR bit a bit|  
|&#124;|OR bit a bit|  
|&&|AND lógico|  
|&#124;&#124;|OR lógico|  
|?:|Condicional|  
|= *OP*=|Asignación, asignación con operación (como += y &=)|  
|,|Evaluación múltiple|  
  
 Los paréntesis se usan para modificar el orden de evaluación determinado por la prioridad de los operadores. Esto significa que una expresión encerrada entre paréntesis se evalúa por completo antes de usar su valor en el resto de la expresión.  
  
 Por ejemplo:  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 En la primera expresión hay tres operadores: =, * y +. Según las normas de precedencia de operadores, se evalúan en el siguiente orden: \*, +, = (78 \* 96 = 7488, 7488 + 3 = 7491).  
  
 En la segunda expresión, el operador ( ) se evalúa primero, por lo que la expresión de suma se evalúa antes que la multiplicación (9 + 3 = 12, 12 * 78 = 936).  
  
 En el siguiente ejemplo se muestra una instrucción que incluye una serie de operadores y se resuelve en `true`.  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Los operadores se evalúan en este orden: ( ) para la agrupación, *, + (dentro de la agrupación), "." para la función, ( ) para la función, /, ==, === y &&.