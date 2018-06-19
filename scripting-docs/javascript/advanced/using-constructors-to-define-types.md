---
title: Uso de constructores para definir tipos | Microsoft Docs
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
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569185"
---
# <a name="using-constructors-to-define-types"></a>Utilizar constructores para definir tipos
Un constructor es una función que crea instancias de un tipo determinado de [objeto](../../javascript/objects-and-arrays-javascript.md). Invoque un constructor con la palabra clave **new**. A continuación se muestran algunos ejemplos de constructores con objetos integrados y objetos personalizados de JavaScript.  
  
## <a name="constructor-examples"></a>Ejemplos de constructor  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 La función constructora contiene la palabra clave **this**, que es una referencia a un objeto vacío recién creado. Inicializa el nuevo objeto creando propiedades y asignándoles valores iniciales. El constructor devuelve una referencia al objeto construido.  
  
## <a name="writing-constructors"></a>Escribir constructores  
 Puede crear objetos mediante el operador **new** junto con funciones constructoras predefinidas como **Object()**, **Date()** y **Function()**. También puede crear funciones constructoras personalizadas que definan un conjunto de propiedades y métodos. A continuación se muestra un ejemplo de un constructor personalizado.  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Cuando se invoca el constructor Circle, se proporcionan valores para el punto central del círculo y el radio. Como resultado se obtiene un objeto Circle que contiene tres propiedades. Así es como se crean instancias de un objeto Circle.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 El tipo de los objetos creados con un constructor personalizado es `object`. Solo hay seis tipos en JavaScript: `object`, `function`, `string`, `number`, `boolean` y `undefined`. Para obtener más información, vea [typeof (Operador de JavaScript)](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso del método bind](../../javascript/advanced/using-the-bind-method-javascript.md)