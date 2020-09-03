---
title: Crear comentarios JSDoc para IntelliSense para JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619271"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Crear comentarios JSDoc para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense en Visual Studio muestra la información que usted agrega a un script mediante comentarios de JSDoc estándar. Puede utilizar comentarios de JSDoc para proporcionar información acerca de elementos de código, como funciones, campos y variables.

## <a name="jsdoc-comment-tags"></a>Etiquetas de comentarios de JSDoc
 IntelliSense utiliza las siguientes etiquetas de comentarios de JSDoc estándar para mostrar información sobre el código.

|  Etiqueta de JSDoc   |                       Sintaxis                        |                                                     Notas                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated*Descripción* de              |                                   Especifica una función o un método en desuso.                                   |
| @description |             @description*Descripción* de              |                              Especifica la descripción de una función o un método.                               |
|    @param    | @param{*Type*} *parameterName*<em>Descripción</em> de ParameterName | Especifica información de un parámetro en una función o un método.<br /><br /> TypeScript también admite @paramTag . |
|  @property   |          @property {*tipo*} *nombreDePropiedad*          |   Especifica la información, incluida una descripción, de un campo o un miembro que se define en un objeto.    |
|   @returns   |                  @returns {*Type*}                  |           Especifica un valor devuelto.<br /><br /> Para TypeScript, use @returnType en lugar de @returns .           |
|   @summary   |               @summary*Descripción* de                |                   Especifica la descripción de una función o un método (igual que @description ).                   |
|    @type     |                   @type {*Type*}                    |                                Especifica el tipo de una constante o una variable.                                |
|   @typedef   |         @typedef {*tipo*} *nombreDeTipoPersonalizado*          |                                            Especifica un tipo personalizado.                                            |

### <a name="examples"></a>Ejemplos
 En el ejemplo siguiente se muestra el uso de las @description @param etiquetas, y @return JSDoc para una función denominada `getArea` .

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

 En el ejemplo siguiente se muestra cómo utilizar la @typedef etiqueta con la @property etiqueta.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 En el ejemplo siguiente se muestra el uso de las @type etiquetas JSDoc. Como se muestra en este ejemplo, no se requieren los asteriscos sencillos (*) que siguen al par inicial de asteriscos (\*\*).

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 En el ejemplo siguiente se muestra cómo usar la @deprecated etiqueta JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
