---
title: "Ámbito de la variable (JavaScript) | Microsoft Docs"
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
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="variable-scope-javascript"></a>Ámbito de la variable (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tiene dos ámbitos: global y local. Una variable que se declara fuera de la definición de una función es una variable global y su valor es accesible y modificable desde su programa. Si se declara dentro de la definición de una función, será local. Se crea y se destruye cada vez que se ejecuta la función y ningún código externo a la función puede tener acceso a ella. JavaScript no admite el ámbito de bloque (en el que un conjunto de llaves `{. . .}` define un nuevo ámbito), excepto en el caso especial de variables de ámbito de bloque.  
  
## <a name="scope-in-javascript"></a>Ámbito en JavaScript  
 Una variable local puede tener el mismo nombre que una variable global, pero es totalmente independiente; el cambio del valor de una variable no tiene efecto en la otra. Solo la versión local tiene significado dentro de la función en que se declara.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 En JavaScript, las variables se evalúan como si se declararan al principio del ámbito en el que existen. Por este motivo, en ocasiones se producen resultados inesperados, como se muestra aquí.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Cuando [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ejecuta una función, primero busca todas las declaraciones de variable, por ejemplo, `var someVariable;`. Crea las variables con un valor inicial de `undefined`. Si una variable se declara con un valor `var someVariable = "something";` por ejemplo, sigue teniendo inicialmente el valor `undefined` y solo adquiere el valor declarado cuando se ejecuta la línea que contiene la declaración.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] procesa todas las declaraciones de variables antes de ejecutar cualquier código, con independencia de que la declaración se encuentre o no dentro de un bloque condicional o de otra construcción. Una vez que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] encuentra todas las variables, ejecuta el código en la función. Si una variable se declara implícitamente dentro de una función (es decir, si aparece en el lado izquierdo de una expresión de asignación pero no se ha declarado con `var`), se crea como variable global.  
  
 En JavaScript, una función interna (anidada) almacena las referencias a las variables locales que se encuentran en el mismo ámbito que la propia función, incluso después de que la función devuelva un valor. Este conjunto de referencias recibe el nombre de cierre. En el ejemplo siguiente, la segunda llamada a la función interna genera el mismo mensaje (“Hello Bill”) que la primera llamada, porque el parámetro de entrada de la función externa, `name`, es una variable local que se almacena en el cierre de la función interna.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>Variables de ámbito del bloque  
 Internet Explorer 11 incluye compatibilidad con [let](../../javascript/reference/let-statement-javascript.md) y [const](../../javascript/reference/const-statement-javascript.md), que son variables de ámbito de bloque. Para estas variables, las llaves `{. . .}` definen un ámbito nuevo. Cuando establezca una de estas variables en un valor específico, el valor solo se aplicará al ámbito en el que se establece.  
  
 En el siguiente ejemplo se muestra el uso de `let` y del ámbito del bloque.  
  
> [!NOTE]
>  El código siguiente se admite en Internet Explorer 11 en modo estándar y versiones posteriores.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```