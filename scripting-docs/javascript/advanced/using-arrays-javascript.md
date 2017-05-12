---
title: "Utilizar matrices (JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript]"
  - "matrices [JavaScript], objetos"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilizar matrices (JavaScript)
Las matrices en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] son *dispersas*.  Es decir, si tienes una matriz con tres elementos numerados como 0, 1 y 2, puedes crear el elemento número 50 sin preocuparte de los elementos del 3 al 49.  Si la matriz tiene una variable automática length \(consulta [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md) para obtener una explicación de la supervisión automática de la longitud de una matriz\), la variable length se establece en 51, no en 4.  Puedes crear matrices en las que no haya huecos en la numeración de los elementos, aunque no es necesario hacerlo.  
  
 En [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], los objetos y las matrices son casi idénticos entre sí.  Las dos diferencias principales son que los objetos que no son matrices no tienen una propiedad de longitud automática y que las matrices no tienen las propiedades y los métodos de un objeto.  
  
## Direccionar matrices  
 Para direccionar matrices se usan corchetes \(\[\]\), como se muestra en el ejemplo siguiente.  Los corchetes rodean un valor numérico o una expresión que se evalúa como un número entero.  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## Objetos como matrices asociativas  
 Normalmente usas el operador punto "." para tener acceso a las propiedades de un objeto.  Por ejemplo,  
  
```javascript  
myObject.aProperty  
```  
  
 En este caso el nombre de propiedad es un identificador.  También puedes tener acceso a las propiedades de un objeto mediante el operador índice \(\[\]\).  En este caso estás tratando el objeto como una *matriz asociativa* en la que los valores de datos están asociados a cadenas.  Por ejemplo,  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 El operador índice suele estar más asociado al acceso a elementos de matriz.  Cuando se usa con objetos, el índice es un literal de cadena que representa el nombre de propiedad.  
  
 Observa las importantes diferencias que existen entre las dos maneras de tener acceso a propiedades de objeto.  
  
1.  Un nombre de propiedad tratado como un identificador \(la sintaxis de punto \(.\)\) no se puede manipular como datos.  
  
2.  Un nombre de propiedad tratado como un índice \(la sintaxis de corchetes \(\[\]\)\) se puede manipular como datos.  
  
 Esta diferencia resulta útil cuando no sabes cuáles serán los nombres de propiedad hasta el momento de la ejecución \(por ejemplo, cuando construyes objetos basados en datos especificados por el usuario\).  Para extraer todas las propiedades de una matriz asociativa, debes usar el bucle `for…in`.