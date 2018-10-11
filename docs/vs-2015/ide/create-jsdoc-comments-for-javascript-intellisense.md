---
title: Crear comentarios JSDoc para IntelliSense para JavaScript | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e24338a75dd631cee86ea8ac81e774e81732bba5
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878997"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Crear comentarios JSDoc para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](/visualstudio/).  
  
IntelliSense en Visual Studio muestra la información que usted agrega a un script mediante comentarios de JSDoc estándar. Puede utilizar comentarios de JSDoc para proporcionar información acerca de elementos de código, como funciones, campos y variables.  
  
## <a name="jsdoc-comment-tags"></a>Etiquetas de comentarios de JSDoc  
 IntelliSense utiliza las siguientes etiquetas de comentarios de JSDoc estándar para mostrar información sobre el código.  
  
|Etiqueta de JSDoc|Sintaxis|Notas|  
|---------------|------------|-----------|  
|@deprecated|@deprecated *Descripción*|Especifica una función o un método en desuso.|  
|@description|@description *Descripción*|Especifica la descripción de una función o un método.|  
|@param|@param {*tipo*} *parameterName ** descripción*|Especifica información de un parámetro en una función o un método.<br /><br /> TypeScript también admite @paramTag.|  
|@property|@property {*tipo*} *propertyName*|Especifica la información, incluida una descripción, de un campo o un miembro que se define en un objeto.|  
|@returns|@returns {*tipo*}|Especifica un valor devuelto.<br /><br /> Para TypeScript, use @returnType en lugar de @returns.|  
|@summary|@summary *Descripción*|Especifica la descripción de una función o método (igual que @description).|  
|@type|@type {*tipo*}|Especifica el tipo de una constante o una variable.|  
|@typedef|@typedef {*tipo*} *customTypeName*|Especifica un tipo personalizado.|  
  
### <a name="examples"></a>Ejemplos  
 El ejemplo siguiente muestra el uso de la @description, @param, y @return JSDoc etiquetas para una función denominada `getArea`.  
  
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
  
 ![Información de IntelliSense para una función](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  
  
 El ejemplo siguiente muestra cómo usar el @typedef etiquetar con el @property etiqueta.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 El ejemplo siguiente muestra el uso de la @type etiquetas de JSDoc. Como se muestra en este ejemplo, único asteriscos (*) que siguen a la par inicial de asteriscos (\*\*) no son necesarios.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 El ejemplo siguiente muestra cómo usar el @deprecated la etiqueta de JSDoc.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```



