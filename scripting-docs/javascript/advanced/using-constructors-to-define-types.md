---
title: "Utilizar constructores para definir tipos | Microsoft Docs"
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
helpviewer_keywords: 
  - "funciones constructoras"
  - "constructores, crear"
  - "crear objetos, funciones constructoras"
  - "funciones, funciones constructoras"
  - "objetos, crear [JavaScript]"
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Utilizar constructores para definir tipos
Un constructor es una función que crea instancias de un tipo determinado de [objeto](../../javascript/objects-and-arrays-javascript.md).  Invoque un constructor con la palabra clave **new**.  A continuación se muestran algunos ejemplos de constructores con objetos integrados y objetos personalizados de JavaScript.  
  
## Ejemplos de constructor  
  
```javascript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 La función constructora contiene la palabra clave **this**, que es una referencia a un objeto vacío recién creado.  Inicializa el nuevo objeto creando propiedades y asignándoles valores iniciales.  El constructor devuelve una referencia al objeto construido.  
  
## Escribir constructores  
 Puede crear objetos mediante el operador **new** junto con funciones predefinidas de constructor como **Object\(\)**, **Date\(\)** y **Function\(\)**.  También puede crear funciones constructoras personalizadas que definan un conjunto de propiedades y métodos.  A continuación se muestra un ejemplo de un constructor personalizado.  
  
```javascript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Cuando se invoca el constructor Circle, se proporcionan valores para el punto central del círculo y el radio.  Como resultado se obtiene un objeto Circle que contiene tres propiedades.  Así es como se crean instancias de un objeto Circle.  
  
```javascript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 El tipo de los objetos creados con un constructor personalizado es `object`.  Solo hay seis tipos en JavaScript: `object`, `function`, `string`, `number`, `boolean` y `undefined`.  Para obtener más información, vea [typeof \(Operador\)](../../javascript/reference/typeof-operator-decrementjavascript.md)  
  
## Vea también  
 [Utilizar el método bind](../../javascript/advanced/using-the-bind-method-javascript.md)