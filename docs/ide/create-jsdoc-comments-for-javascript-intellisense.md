---
title: "Crear comentarios JSDoc para IntelliSense para JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Crear comentarios JSDoc para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense en Visual Studio muestra la información que usted agrega a un script mediante comentarios de JSDoc estándar.  Puede utilizar comentarios de JSDoc para proporcionar información acerca de elementos de código, como funciones, campos y variables.  
  
## Etiquetas de comentarios de JSDoc  
 IntelliSense utiliza las siguientes etiquetas de comentarios de JSDoc estándar para mostrar información sobre el código.  
  
|Etiqueta de JSDoc|Sintaxis|Notas|  
|-----------------------|--------------|-----------|  
|@deprecated|@deprecated *description*|Especifica una función o un método desusado.|  
|@description|@description *description*|Especifica la descripción de una función o un método.|  
|@param|@param {*type*} *parameterName**description*|Especifica información de un parámetro en una función o un método.<br /><br /> TypeScript también admite @paramTag.|  
|@property|@property {*type*} *propertyName*|Especifica la información, incluida una descripción, de un campo o un miembro que se define en un objeto.|  
|@returns|@returns {*type*}|Especifica un valor devuelto.<br /><br /> Para TypeScript, use @returnType en lugar de @returns.|  
|@summary|@summary *description*|Especifica la descripción de una función o un método \(igual que @description\).|  
|@type|@type {*type*}|Especifica el tipo de una constante o una variable.|  
|@typedef|@typedef {*type*} *customTypeName*|Especifica un tipo personalizado.|  
  
### Ejemplos  
 En el ejemplo siguiente se muestra el uso de las etiquetas @description, @param y @return de JSDoc para una función denominada `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 En el ejemplo anterior, IntelliSense muestra la descripción, el parámetro y devuelve información al escribir el paréntesis de apertura de `getArea`.  
  
 ![Información de IntelliSense para una función](~/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 En el siguiente ejemplo se muestra cómo usar la etiqueta @typedef con la etiqueta @property.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 En el siguiente ejemplo se muestra el uso de las etiquetas @type de JSDoc.  Tal como se muestra en este ejemplo, no se requieren los asteriscos sencillos \(\*\) que siguen al par inicial de asteriscos \(\*\).  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 En el siguiente ejemplo se muestra cómo utilizar la etiqueta @deprecated de JSDoc.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```