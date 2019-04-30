---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98bf86f807874fefe066ed2d1008e31451fbbba0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558416"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica información de documentación para una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Opcional. Tipo de datos de la variable. El tipo puede ser uno de los siguientes:  
  
- Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
- Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
- Una función constructora de JavaScript.  
  
  `integer`  
  Opcional. Si `type` es `Number`, especifica si la variable es un entero. Establézcalo en `true` para indicar que la variable es un entero; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `domElement`  
  Opcional. Este atributo está desusado; el atributo `type` tiene prioridad sobre este. Este atributo especifica si la variable documentada es un elemento DOM. Establézcalo en `true` para especificar que la variable es un elemento DOM; de lo contrario, establézcalo en `false`. Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata la variable documentada como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `mayBeNull`  
  Opcional. Especifica si la variable documentada se puede establecer en NULL. Establézcalo en `true` para indicar que la variable se puede establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementType`  
  Opcional. Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
  `elementInteger`  
  Opcional. Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros. Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementDomElement`  
  Opcional. Este atributo está desusado; el atributo `elementType` tiene prioridad sobre este. Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM. Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`. Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `elementMayBeNull`  
  Opcional. Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL. Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `helpKeyword`  
  Opcional. Palabra clave de la Ayuda de F1.  
  
  `locid`  
  Opcional. Identificador de la información de localización sobre la variable. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en la etiqueta [\<loc>](../ide/loc-javascript.md).  
  
  `description`  
  Opcional. Descripción de la variable.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el elemento `<var>`.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
