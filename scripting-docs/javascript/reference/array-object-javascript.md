---
title: Array (objeto de JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Array (Objeto de JavaScript)
Permite la creación de matrices de cualquier tipo de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Array`.  
  
 `size`  
 Opcional. Se refiere al tamaño de la matriz. Como las matrices tienen base cero, los elementos creados tendrán índices desde cero hasta `size` -1.  
  
 `element0,...,elementN`  
 Opcional. Elementos que se van a colocar en la matriz. Esto crea una matriz con  *n*  + 1 elementos y un `length` de  *n*  + 1. Con esta sintaxis, debe proporcionar más de un elemento.  
  
## <a name="remarks"></a>Comentarios  
 Después de crear una matriz, puede acceder a sus elementos individuales mediante la notación [ ]. Tenga en cuenta que las matrices de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] están basadas en cero.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Puede pasar un entero de 32 bits sin signo al constructor `Array` para especificar el tamaño de la matriz. Si el valor es negativo o no es un entero, se produce un error en tiempo de ejecución. Si ejecuta el código siguiente, debería ver este error en la consola.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Si se pasa un solo valor al constructor `Array` y ese valor no es un número, la propiedad `length` se establece en 1 y el valor de ese elemento será el único argumento que se va a pasar.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Las matrices de JavaScript son matrices dispersas, lo que significa que no todos los elementos de una matriz pueden contener datos. En JavaScript, solo los elementos que realmente contienen datos están presentes en la matriz. Esto reduce la cantidad de memoria que utiliza la matriz.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Algunos miembros de las listas siguientes se presentaron en versiones posteriores. Para obtener más información, consulte [información de versión](../../javascript/reference/javascript-version-information.md) o la documentación de los miembros individuales.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Array`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor (propiedad)](../../javascript/reference/constructor-property-array.md)|Especifica la función que crea una matriz.|  
|[length (Propiedad, Array)](../../javascript/reference/length-property-array-javascript.md)|Devuelve un valor entero que supera en uno al elemento mayor definido en una matriz.|  
|[prototype (propiedad)](../../javascript/reference/prototype-property-array.md)|Devuelve una referencia al prototipo para una matriz.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se describen las funciones del objeto `Array`.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[Función Array.From](../../javascript/reference/array-from-function-array-javascript.md)|Devuelve una matriz de un objeto iterable o similar a una matriz.|  
|[Array.isArray (Función)](../../javascript/reference/array-isarray-function-javascript.md)|Devuelve un valor de tipo booleano que indica si un objeto es una matriz.|  
|[Función Array.of](../../javascript/reference/array-of-function-array-javascript.md)|Devuelve una matriz de los argumentos pasados.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[concat (Método, Array)](../../javascript/reference/concat-method-array-javascript.md)|Devuelve una matriz nueva que se compone de una combinación de dos matrices.|  
|[Método Entries](../../javascript/reference/entries-method-array-javascript.md)|Devuelve un iterador que contiene los pares clave-valor de la matriz.|  
|[every (Método)](../../javascript/reference/every-method-array-javascript.md)|Comprueba si una función de devolución de llamada definida devuelve `true` para todos los elementos de una matriz.|  
|[Fill (método)](../../javascript/reference/fill-method-array-javascript.md)|Rellena una matriz con un valor especificado.|  
|[filter (Método)](../../javascript/reference/filter-method-array-javascript.md)|Llama a una función de devolución de llamada definida para cada elemento de una matriz y devuelve una matriz de aquellos valores para los que esa función devuelve `true`.|  
|[findIndex (método)](../../javascript/reference/findindex-method-array-javascript.md)|Devuelve un valor de índice del primer elemento de matriz que cumple los criterios de prueba especificados en una función de devolución de llamada.|  
|[forEach (Método)](../../javascript/reference/foreach-method-array-javascript.md)|Llama a una función de devolución de llamada definida para cada elemento de una matriz.|  
|[hasOwnProperty (Método)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[indexOf (Método, Array)](../../javascript/reference/indexof-method-array-javascript.md)|Devuelve el índice de la primera aparición de un valor de una matriz.|  
|[isPrototypeOf (método)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[join (Método)](../../javascript/reference/join-method-array-javascript.md)|Devuelve un objeto `String` formado por todos los elementos de una matriz concatenados.|  
|[Método Keys](../../javascript/reference/keys-method-array-javascript.md)|Devuelve un iterador que contiene los valores de índice de la matriz.|  
|[lastIndexOf (Método, Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|Devuelve el índice de la última aparición de un valor especificado de una matriz.|  
|[map (Método)](../../javascript/reference/map-method-array-javascript.md)|Llama a una función de devolución de llamada definida para cada elemento de una matriz y devuelve una matriz que contiene los resultados.|  
|[pop (Método)](../../javascript/reference/pop-method-array-javascript.md)|Quita el último elemento de una matriz y lo devuelve.|  
|[propertyIsEnumerable (Método)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[push (Método)](../../javascript/reference/push-method-array-javascript.md)|Anexa nuevos elementos a una matriz y devuelve la nueva longitud de la matriz.|  
|[reduce (Método)](../../javascript/reference/reduce-method-array-javascript.md)|Acumula un solo resultado mediante la llamada a una función de devolución de llamada definida para todos los elementos de una matriz. El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como un argumento en la siguiente llamada a dicha función.|  
|[reduceRight (Método)](../../javascript/reference/reduceright-method-array-javascript.md)|Acumula un solo resultado mediante la llamada a una función de devolución de llamada definida para todos los elementos de una matriz, en orden descendente. El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como un argumento en la siguiente llamada a dicha función.|  
|[reverse (Método)](../../javascript/reference/reverse-method-javascript.md)|Devuelve un objeto `Array` con los elementos invertidos.|  
|[shift (Método)](../../javascript/reference/shift-method-array-javascript.md)|Quita el primer elemento de una matriz y lo devuelve.|  
|[slice (Método, Array)](../../javascript/reference/slice-method-array-javascript.md)|Devuelve una sección de una matriz.|  
|[some (Método)](../../javascript/reference/some-method-array-javascript.md)|Comprueba si una función de devolución de llamada definida devuelve `true` para cualquier elemento de una matriz.|  
|[sort (Método)](../../javascript/reference/sort-method-array-javascript.md)|Devuelve un objeto `Array` con los elementos ordenados.|  
|[splice (Método)](../../javascript/reference/splice-method-array-javascript.md)|Quita elementos de una matriz, inserta nuevos elementos en su lugar si procede y devuelve los elementos eliminados.|  
|[toLocaleString (Método)](../../javascript/reference/tolocalestring-method-object-javascript.md)|Devuelve una cadena con la configuración regional actual.|  
|[toString (método)](../../javascript/reference/tostring-method-array.md)|Devuelve una representación de cadena de una matriz.|  
|[unshift (Método)](../../javascript/reference/unshift-method-array-javascript.md)|Inserta nuevos elementos al principio de una matriz.|  
|[valueOf (método)](../../javascript/reference/valueof-method-array.md)|Obtiene una referencia a la matriz.|  
|[Método Values](../../javascript/reference/values-method-array-javascript.md)|Devuelve un iterador que contiene los valores de la matriz.|  
  
## <a name="see-also"></a>Vea también  
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)