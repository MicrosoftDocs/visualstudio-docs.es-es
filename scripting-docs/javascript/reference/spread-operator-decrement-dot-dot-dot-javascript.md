---
title: "Operador Spread (...) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Operador Spread (...) (JavaScript)
Permite que partes de una matriz literal se inicialicen desde una expresión iterable \(como, por ejemplo, otra matriz literal\) o permite que una expresión se expanda a varios argumentos \(en llamadas a funciones\).  
  
## Sintaxis  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## Parámetros  
 `iterable`  
 Requerido.  Un objeto iterable.  
  
 `arg0ToN`  
 Opcional.  Uno o más elementos de un literal de matriz.  
  
 `args`  
 Opcional.  Uno o más argumentos a una función.  
  
## Comentarios  
 Para obtener más información sobre iteradores, vea [Iteradores y generadores](../../javascript/advanced/iterators-and-generators-javascript.md).  Para obtener más información sobre cómo utilizar el operador spread como un parámetro rest, consulte [Funciones](../../javascript/functions-javascript.md).  
  
## Ejemplo  
 En el ejemplo de código mostrado a continuación, el uso del operador spread se contrasta con el uso del método `concat`.  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## Ejemplo  
 En el ejemplo de código mostrado a continuación se indica cómo utilizar el operador spread en una llamada de función.  En este ejemplo dos literales de matriz se pasan a la función mediante el operador spread y las matrices se expanden a varios argumentos.  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## Ejemplo  
 Con los operadores spread, puede simplificar código que anteriormente requería el uso de `apply`.  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)