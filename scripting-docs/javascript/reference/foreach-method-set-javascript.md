---
title: "forEach (método, Set) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>forEach (Método, Set de JavaScript)
Realiza la acción especificada para cada elemento de un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `setObj`  
 Obligatorio. Objeto `Set`.  
  
 `callbackfn`  
 Obligatorio. `callbackfn`acepta hasta tres argumentos. La función que `forEach` llama una vez para cada elemento en el conjunto.  
  
 `thisArg`  
 Opcional. Un objeto que la `this` palabra clave puede hacer referencia a en el `callbackfn` (función). Si se omite `thisArg`, se usa `undefined` como valor `this`.  
  
## <a name="exceptions"></a>Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, key, setObj)`  
  
 Puede declarar la función de devolución de llamada usando hasta tres parámetros, tal como se muestra en la tabla siguiente.  
  
|Argumento de devolución de llamada|Definición|  
|-----------------------|----------------|  
|`value`|Un valor contenido en el conjunto.|  
|`key`|Un valor contenido en el conjunto. Un conjunto no tiene ninguna clave, por lo que este valor es el mismo que `value`.|  
|`setObj`|La `Set` objeto atravesar.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar `forEach`. El `callbackfn` argumento incluye el código para la función de devolución de llamada.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra que se pueden recuperar a los miembros de un conjunto pasando un solo parámetro a la función de devolución de llamada.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]