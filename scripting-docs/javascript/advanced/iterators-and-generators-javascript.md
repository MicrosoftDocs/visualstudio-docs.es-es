---
title: "Iteradores y generadores (JavaScript) | Microsoft Docs"
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
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Iteradores y generadores (JavaScript)
Un iterador es un objeto que se usa para atravesar un objeto de contenedor como una lista.  En JavaScript, un objeto de iterador no es un objeto integrado diferenciado, sino un objeto que implementa un método `next` para tener acceso al elemento siguiente en el objeto contenedor.  
  
 En [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] puede crear sus propios iteradores personalizados.  Sin embargo, suele ser mucho más fácil usar generadores, ya que simplifican enormemente la creación de iteradores.  Los generadores son un tipo de función que es una fábrica de iteradores.  Para crear un iterador personalizado con una función de generador, vea [Generadores](#Generators).  
  
> [!CAUTION]
>  Los generadores son compatibles con [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Iteradores  
 La implementación de un iterador de JavaScript implica dos o tres objetos que se ajustan a interfaces específicas:  
  
-   Interfaz Iterable  
  
-   Interfaz Iterator  
  
-   Interfaz IteratorResult  
  
 Con estas interfaces se pueden crear iteradores personalizados.  Esto le permite recorrer un objeto iterable mediante la instrucción `for…of`.  
  
### Interfaz Iterable  
 La interfaz Iterable es la interfaz necesaria para un objeto iterable \(un objeto para el que se puede obtener un iterador\).  Por ejemplo, `C` en `for (let e of C)` debe implementar la interfaz Iterable.  
  
 Un objeto iterable debe proporcionar el método Symbol.iterator, que devuelve un iterador.  
  
```javascript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Esta propiedad debe ser una función que no acepte argumentos y devuelva un objeto \(`iterObject`\) que se ajusta a la interfaz `Iterator`.  
  
 Muchos tipos integrados, incluidas las matrices, ahora son iterables.  El bucle `for…of` consume un objeto iterable.  \(Sin embargo, no todos los iterables integrados son iteradores.  Por ejemplo, un objeto Array no es un iterador en sí mismo, pero es iterable, mientras que un ArrayIterator también es iterable\).  
  
### Interfaz Iterator  
 El objeto devuelto por el método Symbol.iterator debe implementar el método `next`.  El método `next` tiene la siguiente sintaxis.  
  
```javascript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 El método `next` es una función que devuelve un valor.  La función devuelve un objeto \(`iterResultObj`\) que se ajusta a la interfaz `IteratorResult`.  Si una llamada anterior al método `next` de un iterador devolvió un objeto `IteratorResult` cuya propiedad `done` es true, se finaliza la iteración y el método `next` no se llama de nuevo.  
  
 Los iteradores también pueden incluir un método `return` para asegurarse de que el iterador se elimina correctamente cuando el script finaliza con él.  
  
### Interfaz IteratorResult  
 La interfaz IteratorResult es la interfaz necesaria para el resultado del método `next` en un iterador.  El objeto devuelto por `next` debe proporcionar una propiedad `done` y `value`.  
  
```javascript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 La propiedad `done` devuelve el estado de una llamada de método `next` de iterador, ya sea true o false.  Si se alcanzó el final del iterador, `done` devuelve true.  Si no se alcanzó el final, `done` devuelve false y el valor está disponible.  Si la propiedad `done` \(ya sea su propiedad o una heredada\) no existe, el resultado de `done` se trata como false.  
  
 Si `done` es false, la propiedad `value` devuelve el valor del elemento de iteración actual.  Si `done` es true, este es el valor devuelto del iterador, si se proporciona un valor devuelto.  Si el iterador no tiene un valor devuelto, `value` no está definido.  En ese caso, la propiedad `value` puede no estar presente en el objeto de conformidad si no hereda una propiedad value explícita.  
  
<a name="Generators"></a>   
## Generadores  
 Para crear y usar iteradores personalizados de forma fácil, cree una función generator mediante la sintaxis de function\* junto con una o más expresiones `yield`.  La función generator devuelve un iterador \(es decir, un generador\), lo que permite que el cuerpo de la función generator se ejecute.  La función se ejecuta a la siguiente instrucción `yield` o `return`.  
  
 Llame al método `next` del iterador para devolver el siguiente valor de la función generator.  
  
 En el ejemplo siguiente se muestra un generador que devuelve un iterador para un objeto de cadena.  
  
```javascript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 En un generador, la expresión de operando yield finaliza la llamada a `next` y devuelve un objeto `IteratorResult` con dos propiedades, `done` \(`done=false`\) y `value` \(`value=operand`\).  `operand` es opcional y, si está ausente, su valor es indefinido.  
  
 En un generador, una instrucción `return` instrucción finaliza el generador devolviendo `IteratorResult` con `done=true` junto con el resultado de operando opcional para la propiedad value.  
  
 También puede usar una expresión `yield*` en lugar de `yield` para delegar a otro generador o a otro objeto iterable, como una matriz o una cadena.  
  
 Si anexa el siguiente código al ejemplo anterior, `yield*` delega en el generador `stringIter`.  
  
```javascript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 También puede crear generadores más avanzados si pasa un argumento a `next` y usa el argumento para modificar el estado del generador.  `next` se convierte en el valor del resultado de la expresión `yield` ejecutada anteriormente.  En el siguiente ejemplo, cuando se pasa un valor de 100 al método `next`, se restablece el valor de índice interno del generador.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }  
  
var si3 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 Otros generadores avanzados pueden llamar al método `throw` del generador.  El error que se produce parece originarse cuando el generador se pausa \(antes de la siguiente instrucción `yield`\).