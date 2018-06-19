---
title: Copiar, pasar y comparar datos (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], passing values
- function parameters
- string comparison
- function parameters, about function parameters
- ByRef argument
- arrays [Visual Studio], setting data types
- arrays [Visual Studio], copying data
- ByVal argument
- string comparison, testing data
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3cf980ca1dfd0c0e09871b6de9756cb2a10364b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569335"
---
# <a name="copying-passing-and-comparing-data-javascript"></a>Copiar, pasar y comparar datos (JavaScript)
En [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], la forma en que se controlan los datos depende del tipo de datos.  
  
## <a name="by-value-vs-by-reference"></a>Por valor frente a por referencia  
 Los números y valores booleanos (**true** y **false**) se copian, pasan y comparan *por valor*. Al copiar o pasar por valor, se asigna un espacio en la memoria del equipo y se copia en él el valor del original. Si después se cambia el original, la copia no se ve afectada (y viceversa) porque son dos entidades independientes.  
  
 Los objetos, las matrices y las funciones se copian, pasan y comparan *por referencia*. Al copiar o pasar por referencia, básicamente se crea un puntero al elemento original y se usa el puntero como si fuera una copia. Si después se cambia el original, se cambia tanto el original como la copia (y viceversa). En realidad, solo hay una entidad; la "copia" no es realmente una copia, sino solo otra referencia a los datos.  
  
 Al comparar por referencia, las dos variables deben hacer referencia exactamente a la misma entidad para que la comparación se realice correctamente. Por ejemplo, el resultado de una comparación entre dos objetos **Array** distintos siempre será diferente, aunque contengan los mismos elementos. Para que la comparación se realice correctamente, una de las variables debe ser una referencia a la otra. Para verificar si los dos objetos Array contienen los mismos elementos, compare los resultados del método **toString()**.  
  
 Por último, las cadenas se copian y pasan por referencia, pero se comparan por valor. Tenga en cuenta que si tiene dos objetos **String** (creados con **new** String("something")), se comparan por referencia, pero si uno o ambos valores son un valor de cadena, se comparan por valor.  
  
> [!NOTE]
>  Debido a la forma en que se crean los juegos de caracteres ASCII y ANSI, las letras mayúsculas preceden a las letras minúsculas en orden de secuencia. Por ejemplo, "Zoo" es *menor* que "alianza". Puede llamar a **toUpperCase()** o **toLowerCase()** en ambas cadenas si quiere hacer una comparación en la que no se distingan mayúsculas y minúsculas.  
  
## <a name="passing-parameters-to-functions"></a>Pasar parámetros a funciones  
 Cuando se pasa un parámetro a una función por valor, se está realizando una copia independiente del parámetro que solo existe dentro de la función. Aunque los objetos y matrices se pasen por referencia, si se sobrescriben directamente con un nuevo valor en la función, el nuevo valor no se reflejará fuera de la función. Sólo los cambios en las propiedades de los objetos o de los elementos de las matrices son visibles fuera de la función.  
  
 Por ejemplo (usando el modelo de objetos de Internet Explorer):  
  
```JavaScript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## <a name="testing-data"></a>Probar datos  
 Cuando se realiza una comprobación por valor, se comparan dos elementos distintos para ver si son iguales. Normalmente, esta comparación se realiza byte a byte. Cuando se prueba por referencia, se comprueba si dos elementos son punteros a un único elemento original. Si lo son, se comparan como elementos iguales; si no, aunque contengan exactamente los mismos valores, byte a byte, no se comparan como elementos iguales.  
  
 Copiar y pasar cadenas por referencia ahorra memoria; pero como no se pueden cambiar cadenas una vez creadas, es posible compararlas por valor. Esto permite probar si dos cadenas tienen el mismo contenido aunque una se haya generado completamente por separado de la otra.  
  
## <a name="see-also"></a>Vea también  
 [Cálculo de fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)