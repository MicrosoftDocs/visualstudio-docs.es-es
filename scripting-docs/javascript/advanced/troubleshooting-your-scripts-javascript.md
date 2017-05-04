---
title: "Soluci&#243;n de problemas de scripts (JavaScript) | Microsoft Docs"
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
  - "conversión automática de tipos"
  - "solución de problemas en las secuencias de comandos"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Soluci&#243;n de problemas de scripts (JavaScript)
En todos los lenguajes de programación hay aspectos que dan sorpresas.  Por ejemplo, el valor `null` de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no se comporta igual que el valor `Null` de los lenguajes C o C\+\+.  
  
 A continuación se incluyen algunas de las áreas problemáticas con las que te puedes encontrar al escribir scripts de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Errores de sintaxis  
 Es importante prestar atención a los detalles cuando se escriben scripts.  Por ejemplo, las cadenas se deben poner entre comillas.  
  
## Orden de interpretación de los scripts  
 La interpretación de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] forma parte del proceso de análisis de HTML del explorador web.  Si colocas un script dentro de la etiqueta \<HEAD\> de un documento, se interpreta antes que cualquier parte de la etiqueta \<BODY\>.  Si hay objetos que se crean en la etiqueta \<BODY\>, no existen cuando se analiza \<HEAD\>. Por eso, el script no los puede manipular.  
  
> [!NOTE]
>  Este comportamiento es específico de Internet Explorer.  ASP y WSH tienen modelos de ejecución diferentes \(al igual que otros hosts\).  
  
## Conversión automática de tipos  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es un lenguaje con establecimiento flexible de tipos y conversión automática.  Aunque los valores con tipos distintos no son iguales, las expresiones del ejemplo siguiente se evalúan como **true**.  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 Para comprobar que el tipo y el valor coinciden, usa el operador de igualdad estricta \(\=\=\=\).  Los siguientes ejemplos se evalúan como false:  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## Prioridad de operadores  
 La [prioridad de operador](../../javascript/operator-subtractprecedence-javascript.md) determina cuándo se realiza una operación durante la evaluación de una expresión.  En el ejemplo siguiente, la multiplicación se calcula antes que la resta, aunque la resta aparece antes en la expresión.  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## Usar bucles for...in con objetos  
 Al recorrer en iteración las propiedades de un objeto con un bucle [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), no puedes predecir ni controlar el orden en el que se asignan los campos del objeto a la variable contadora del bucle.  Más aún, el orden puede ser distinto en implementaciones diferentes del lenguaje.  
  
## Palabra clave with  
 La instrucción [with](../../javascript/reference/with-statement-javascript.md) es adecuada para tener acceso a propiedades que ya existen en un objeto especificado, pero no se puede usar para agregar propiedades a un objeto.  Para crear nuevas propiedades en un objeto, debes hacer referencia al objeto específicamente.  
  
## Palabra clave this  
 Aunque la palabra clave `this` que hay dentro de la definición de un objeto se usa para hacer referencia a ese mismo objeto, no se puede utilizar `this` ni otras palabras clave parecidas para hacer referencia a la función que se está ejecutando si esa función no es una definición de objeto.  Si la función se va a asignar a un objeto como un método, para hacer referencia al objeto, puedes usar la palabra clave `this` dentro de la función.  
  
## Escribir un script que escribe un script en Internet Explorer  
 La etiqueta \<\/SCRIPT\> termina el script actual en caso de que el intérprete lo encuentre.  Para mostrar el propio "\<\/SCRIPT\>", tienes que escribirlo otra vez al menos en dos cadenas \(por ejemplo, "\<\/SCR" e "IPT\>"\), que luego puedes concatenar juntas en la instrucción que las escribe.  
  
## Referencias implícitas a una ventana en Internet Explorer  
 Como se puede abrir más de una ventana a la vez, cualquier referencia implícita a una ventana apunta a la ventana actual.  Para utilizar otras ventanas, debes utilizar una referencia explícita.