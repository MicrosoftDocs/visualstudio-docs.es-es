---
title: "Array (Objeto de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Array"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array (objeto)"
  - "constructor (propiedad)"
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Array (Objeto de JavaScript)
Proporciona compatibilidad para la creación de matrices de cualquier tipo de datos.  
  
## Sintaxis  
  
```  
  
        arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto `Array`.  
  
 `size`  
 Opcional.  Se refiere al tamaño de la matriz.  Como las matrices son de base cero, los elementos creados tendrán índices desde cero hasta `size` \-1.  
  
 `element0,...,elementN`  
 Opcional.  Elementos que se van a colocar en la matriz.  Esto crea una matriz con *n* \+ 1 elementos y un valor `length` de *n* \+ 1.  Con esta sintaxis, debe proporcionar más de un elemento.  
  
## Comentarios  
 Después de crear una matriz, puede acceder a sus elementos individuales mediante la notación \[ \].  Tenga en cuenta que las matrices de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] son de base cero.  
  
```javascript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Puede pasar un entero de 32 bits sin signo al constructor `Array` para especificar el tamaño de la matriz.  Si el valor es negativo o no es un entero, se produce un error en tiempo de ejecución.  Si ejecuta el código siguiente, verá este error en la consola.  
  
```javascript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Si se pasa un solo valor al constructor `Array` y no es un número, la propiedad `length` se establece en 1 y el valor de ese elemento se convierte en el único argumento que se pasa.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Las matrices de JavaScript son matrices dispersas, lo que significa que puede que no todos los elementos de una matriz contengan datos.  En JavaScript, solo los elementos que realmente contienen datos están presentes en la matriz.  Esto reduce la cantidad de memoria que usa la matriz.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Algunos miembros de las listas siguientes se introdujeron en versiones posteriores.  Para más información, vea [Información de versiones](../../javascript/reference/javascript-version-information.md) o la documentación de los miembros individuales.  
  
## Propiedades  
 En la tabla siguiente se enumeran las propiedades del objeto `Array`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[Propiedad constructor](../../javascript/reference/constructor-property-array.md)|Especifica la función que crea una matriz.|  
|[Propiedad length \(matriz\)](../../javascript/reference/length-property-array-javascript.md)|Devuelve un valor entero que supera en uno al elemento mayor definido en una matriz.|  
|[Propiedad prototype](../../javascript/reference/prototype-property-array.md)|Devuelve una referencia al prototipo para una matriz.|  
  
## Funciones  
 En la tabla siguiente se describen las funciones del objeto `Array`.  
  
|Función|Descripción|  
|-------------|-----------------|  
|[Función Array.From](../../javascript/reference/array-from-function-array-javascript.md)|Devuelve una matriz de un objeto similar a una matriz o iterable.|  
|[Función Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Devuelve un valor booleano que indica si un objeto es una matriz.|  
|[Función Array.of](../../javascript/reference/array-of-function-array-javascript.md)|Devuelve una matriz de los argumentos pasados.|  
  
<a name="js56jsobjarraymeth"></a>   
## Métodos  
 En la tabla siguiente se enumeran los métodos del objeto `Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método concat \(matriz\)](../../javascript/reference/concat-method-array-javascript.md)|Devuelve una matriz nueva que se compone de una combinación de dos matrices.|  
|[Método entries](../../javascript/reference/entries-method-array-javascript.md)|Devuelve un iterador que contiene los pares clave\-valor de la matriz.|  
|[Método every](../../javascript/reference/every-method-array-javascript.md)|Comprueba si una función de devolución de llamada definida devuelve `true` para todos los elementos de una matriz.|  
|[Método fill](../../javascript/reference/fill-method-array-javascript.md)|Rellena una matriz con un valor especificado.|  
|[Método filter](../../javascript/reference/filter-method-array-javascript.md)|Llama a una función de devolución de llamada definida en cada elemento de una matriz y devuelve una matriz de valores para los que la función de devolución de llamada devuelve `true`.|  
|[Método findIndex](../../javascript/reference/findindex-method-array-javascript.md)|Devuelve un valor de índice del primer elemento de matriz que cumple los criterios de prueba especificados en una función de devolución de llamada.|  
|[Método forEach](../../javascript/reference/foreach-method-array-javascript.md)|Llama a una función de devolución de llamada definida para cada elemento de una matriz.|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[Método IndexOf \(matriz\)](../../javascript/reference/indexof-method-array-javascript.md)|Devuelve el índice de la primera aparición de un valor de una matriz.|  
|[Método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[Método join](../../javascript/reference/join-method-array-javascript.md)|Devuelve un objeto `String` formado por todos los elementos de una matriz concatenados.|  
|[Método keys](../../javascript/reference/keys-method-array-javascript.md)|Devuelve un iterador que contiene los valores de índice de la matriz.|  
|[Método lastIndexOf \(matriz\)](../../javascript/reference/lastindexof-method-array-javascript.md)|Devuelve el índice de la última aparición de un valor especificado de una matriz.|  
|[Método map](../../javascript/reference/map-method-array-javascript.md)|Llama a una función de devolución de llamada definida en cada elemento de una matriz y devuelve una matriz que contiene los resultados.|  
|[Método pop](../../javascript/reference/pop-method-array-javascript.md)|Quita el último elemento de una matriz y lo devuelve.|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si es enumerable.|  
|[Método push](../../javascript/reference/push-method-array-javascript.md)|Anexa elementos nuevos a una matriz y devuelve la nueva longitud de la matriz.|  
|[Método reduce](../../javascript/reference/reduce-method-array-javascript.md)|Acumula un solo resultado llamando a una función de devolución de llamada definida para todos los elementos de una matriz.  El valor devuelto de la función de devolución de llamada es el resultado acumulado y se proporciona como argumento en la llamada siguiente a la función de devolución de llamada.|  
|[Método reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Acumula un solo resultado llamando a una función de devolución de llamada definida para todos los elementos de una matriz en orden descendente.  El valor devuelto de la función de devolución de llamada es el resultado acumulado y se proporciona como argumento en la llamada siguiente a la función de devolución de llamada.|  
|[Método reverse](../../javascript/reference/reverse-method-javascript.md)|Devuelve un objeto `Array` con los elementos invertidos.|  
|[Método shift](../../javascript/reference/shift-method-array-javascript.md)|Quita el primer elemento de una matriz y lo devuelve.|  
|[Método slice \(matriz\)](../../javascript/reference/slice-method-array-javascript.md)|Devuelve una sección de una matriz.|  
|[Método some](../../javascript/reference/some-method-array-javascript.md)|Comprueba si una función de devolución de llamada definida devuelve `true` para cualquier elemento de una matriz.|  
|[Método sort](../../javascript/reference/sort-method-array-javascript.md)|Devuelve un objeto `Array` con los elementos ordenados.|  
|[Método splice](../../javascript/reference/splice-method-array-javascript.md)|Quita los elementos de una matriz y, si es necesario, inserta en su lugar elementos nuevos y devuelve los elementos eliminados.|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Devuelve una cadena usando la configuración regional actual.|  
|[toString \(Método\)](../../javascript/reference/tostring-method-array.md)|Devuelve una representación de cadena de una matriz.|  
|[Método unshift](../../javascript/reference/unshift-method-array-javascript.md)|Inserta elementos nuevos al principio de una matriz.|  
|[Método valueOf](../../javascript/reference/valueof-method-array.md)|Obtiene una referencia a la matriz.|  
|[Método values](../../javascript/reference/values-method-array-javascript.md)|Devuelve un iterador que contiene los valores de la matriz.|  
  
## Vea también  
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)