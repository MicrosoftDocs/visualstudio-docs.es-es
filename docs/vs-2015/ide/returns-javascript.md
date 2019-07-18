---
title: '&lt;Devuelve&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203542"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica información de documentación para el resultado de una llamada de función o de método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Opcional. Tipo de datos del valor devuelto. El tipo puede ser uno de los siguientes:  
  
- Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
- Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
- Una función constructora de JavaScript.  
  
  `integer`  
  Opcional. Si `type` es `Number`, especifica si el valor devuelto es un entero. Establézcalo en `true` para indicar que el valor devuelto es un entero; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `domElement`  
  Opcional. Este atributo está desusado; el atributo `type` tiene prioridad sobre este. Este atributo especifica si el valor devuelto documentado es un elemento DOM. Establézcalo en `true` para especificar que el valor devuelto es un elemento DOM; de lo contrario, establézcalo en `false`. Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata el valor devuelto documentado como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `mayBeNull`  
  Opcional. Especifica si el valor devuelto documentado se puede establecer en NULL. Establézcalo en `true` para indicar que el valor devuelto se puede establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementType`  
  Opcional. Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
  `elementInteger`  
  Opcional. Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros. Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementDomElement`  
  Opcional. Este atributo está desusado; el atributo `elementType` tiene prioridad sobre este. Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM. Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`. Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `elementMayBeNull`  
  Opcional. Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL. Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `locid`  
  Opcional. Identificador para la información de localización sobre el valor devuelto. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en la etiqueta [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  Opcional. Especifica el código que se debe evaluar para uso de IntelliSense en lugar del propio código de función. Por ejemplo, puede utilizar este atributo para proporcionar IntelliSense para las devoluciones de llamada asincrónicas, como `Promise`. El uso del atributo `value` con el elemento `<returns>` puede mejorar el rendimiento de IntelliSense al omitir la ejecución de código largo.  
  
  `description`  
  Opcional. Descripción del valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 El elemento `<returns>` debe colocarse en el cuerpo de la función antes de cualquier instrucción.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el elemento `<returns>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Otras referencias  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
