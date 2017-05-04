---
title: "0...n (Propiedades, arguments de JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propiedades 0...n"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n (Propiedades, arguments de JavaScript)
Devuelve el valor real de argumentos individuales de un objeto **arguments** devuelto por la propiedad **arguments** de una función en ejecución.  
  
## Sintaxis  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## Parámetros  
 *function*  
 Opcional.  Nombre del objeto `Function` que se ejecuta actualmente.  
  
 0, 1, 2, *, n*  
 Obligatorio.  Entero no negativo en el intervalo de 0 a *n*, donde 0 representa el primer argumento y *n* representa el argumento final.  El valor del argumento final *n* es **arguments.length\-1**.  
  
## Comentarios  
 Los valores devueltos por las propiedades 0 .  .  .  n son los valores reales pasados a la función en ejecución.  Aunque no es realmente una matriz de argumentos, se tiene acceso a los argumentos individuales que componen el objeto **arguments** de la misma forma que a los elementos de matriz.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de las propiedades **0 . . .**  ***n*** del objeto **arguments**.  Para comprender totalmente el ejemplo, pasa uno o más argumentos a la función:  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments \(Objeto\)](../../javascript/reference/arguments-object-javascript.md)&#124; [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)  
  
## Vea también  
 [length \(Propiedad, argumentos\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length \(Propiedad, Function\)](../../javascript/reference/length-property-function-javascript.md)