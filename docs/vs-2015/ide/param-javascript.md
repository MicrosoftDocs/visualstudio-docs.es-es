---
title: '&lt;param&gt; (JavaScript) | Documentos de Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20a0f38abd5f1b7479129b8f30f4ae5620f2561f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576168"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Especifica información de documentación de un parámetro en una función o un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 Requerido. Nombre del parámetro.  
  
 `type`  
 Opcional. Tipo de datos del parámetro. El tipo puede ser uno de los siguientes:  
  
-   Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
-   Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
-   Una función constructora de JavaScript.  
  
 `integer`  
 Opcional. Si `type` es `Number`, especifica si el parámetro es un entero. Establézcalo en `true` para indicar que el parámetro es un entero; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `domElement`  
 Opcional. Este atributo está desusado; el atributo `type` tiene prioridad sobre este. Este atributo especifica si el parámetro documentado es un elemento DOM. Establézcalo en `true` para especificar que el parámetro es un elemento DOM; de lo contrario, establézcalo en `false`. Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata el parámetro documentado como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `mayBeNull`  
 Opcional. Especifica si el parámetro documentado se puede establecer en NULL. Establézcalo en `true` para indicar que el parámetro se puede establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementType`  
 Opcional. Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
 `elementInteger`  
 Opcional. Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros. Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementDomElement`  
 Opcional. Este atributo está desusado; el atributo `elementType` tiene prioridad sobre este. Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM. Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`. Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `elementMayBeNull`  
 Opcional. Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL. Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `locid`  
 Opcional. Identificador de la información de localización sobre el parámetro. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `parameterArray`  
 Opcional. Especifica si el parámetro documentado se puede repetir en la llamada de función, similar a los parámetros repetidos que se admiten en la función `String.format`. Establézcalo en `true` para indicar que el parámetro se puede repetir; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `optional`  
 Opcional. Especifica si el parámetro documentado es opcional en la función de llamada. Establézcalo en `true` para indicar que el parámetro es opcional; de lo contrario, establézcalo en `false`.  
  
 `value`  
 Opcional. Especifica el código que se debe evaluar para uso de IntelliSense en lugar del propio código de función. Puede utilizar este atributo para proporcionar información de tipos cuando el tipo de parámetro es indefinido. Por ejemplo, puede usar `value=’1’` para tratar el tipo de parámetro como un número.  
  
 `description`  
 Opcional. Descripción del parámetro.  
  
## <a name="remarks"></a>Comentarios  
 El único atributo obligatorio es `name`. Todos los demás atributos son opcionales.  
  
 Elementos utilizados para anotar funciones, como [ \<resumen >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), y [ \<devuelve >](../ide/returns-javascript.md), se deben colocar en el cuerpo de la función antes de cualquier instrucción.  
  
 Si hay varios elementos `<param>` que tienen el mismo nombre, se utiliza uno de los elementos `<param>` y se omiten los elementos redundantes. El comportamiento que determina qué elemento se utiliza no está definido. Si `name` hace referencia a un parámetro inexistente, se omite el elemento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el elemento `<param>`.  
  
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
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)



