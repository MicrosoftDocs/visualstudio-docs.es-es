---
title: Uso de matrices (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="using-arrays-javascript"></a>Utilizar matrices (JavaScript)
Las matrices de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] son *dispersas*. Es decir, si tiene una matriz con tres elementos que están numerados 0, 1 y 2, puede crear el elemento 50 sin preocuparse por los elementos del 3 al 49. Si la matriz tiene una variable de longitud automática (consulte sobre los [objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md) para obtener una explicación de la supervisión automática de la longitud de matriz), la variable de longitud se establece en 51, en lugar de en 4. Si bien puede crear matrices en las que no haya ningún hueco en la numeración de los elementos, no es necesario hacerlo.  
  
 En [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], los objetos y las matrices son casi idénticos entre sí. Las dos diferencias principales son que los objetos que no son de matriz no tienen una propiedad de longitud automática y las matrices no tiene las propiedades y los métodos de un objeto.  
  
## <a name="addressing-arrays"></a>Direccionamiento de matrices  
 Las matrices se direccionan mediante corchetes ([]), como se muestra en el ejemplo siguiente. Los corchetes encierran un valor numérico o una expresión que se evalúa como un número entero.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Objetos como matrices asociativas  
 Por lo general, el operador punto "." se usa para acceder a las propiedades de un objeto. Por ejemplo,  
  
```JavaScript  
myObject.aProperty  
```  
  
 En este caso, el nombre de propiedad es un identificador. También puede acceder a las propiedades de un objeto mediante el operador de índice ([]). En este caso, el objeto se trata como una *matriz asociativa* en la que los datos están asociados con cadenas. Por ejemplo,  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 El operador de índice suele estar más comúnmente asociado con el acceso a los elementos de la matriz. Cuando se usa con objetos, el índice es un literal de cadena que representa el nombre de la propiedad.  
  
 Tenga en cuenta las diferencias importantes entre las dos maneras de acceder a las propiedades del objeto.  
  
1.  Un subproceso de nombre de propiedad tratado como un identificador (la sintaxis punto (.)) no se puede manipular como datos.  
  
2.  Un nombre de propiedad que se trata como un índice (sintaxis [])) se puede manipular como datos.  
  
 Esta diferencia resulta útil cuando no se sabe cuáles serán los nombres de las propiedades hasta que tenga lugar el tiempo de ejecución (por ejemplo, cuando va a construir objetos basados en la entrada de usuario). Para extraer todas las propiedades de una matriz asociativa, debe usar el bucle `for...in`.
