---
title: Crear comentarios JSDoc para IntelliSense para JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 22db62a186c1f1c668a0304a9b586aca85e713c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758518"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Crear comentarios JSDoc para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense en Visual Studio muestra la información que usted agrega a un script mediante comentarios de JSDoc estándar. Puede utilizar comentarios de JSDoc para proporcionar información acerca de elementos de código, como funciones, campos y variables.  

## <a name="jsdoc-comment-tags"></a>Etiquetas de comentarios de JSDoc  
 IntelliSense utiliza las siguientes etiquetas de comentarios de JSDoc estándar para mostrar información sobre el código.  


|  Etiqueta de JSDoc   |                       Sintaxis                        |                                                     Notas                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *descripción*              |                                   Especifica una función o un método en desuso.                                   |
| @description |             @description *descripción*              |                              Especifica la descripción de una función o un método.                               |
|    @param    | @param {*tipo*} *parameterName*<em>descripción</em> | Especifica información de un parámetro en una función o un método.<br /><br /> TypeScript también admite @paramTag. |
|  @property   |          @property {*tipo*} *nombreDePropiedad*          |   Especifica la información, incluida una descripción, de un campo o un miembro que se define en un objeto.    |
|   @returns   |                  @returns {*tipo*}                  |           Especifica un valor devuelto.<br /><br /> Para TypeScript, use @returnType en lugar de @returns.           |
|   @summary   |               @summary *descripción*                |                   Especifica la descripción de una función o método (igual que @description).                   |
|    @type     |                   @type {*tipo*}                    |                                Especifica el tipo de una constante o una variable.                                |
|   @typedef   |         @typedef {*tipo*} *nombreDeTipoPersonalizado*          |                                            Especifica un tipo personalizado.                                            |

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

 El ejemplo siguiente muestra el uso de la @type etiquetas de JSDoc. Como se muestra en este ejemplo, no se requieren los asteriscos sencillos (*) que siguen al par inicial de asteriscos (\*\*).  

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
