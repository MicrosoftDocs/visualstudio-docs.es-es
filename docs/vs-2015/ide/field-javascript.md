---
title: '&lt;campo&gt; (JavaScript) | Documentos de Microsoft'
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
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 155d3e771362949288d31a20245c7fb45a022969
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880979"
---
# <a name="ltfieldgt-javascript"></a>&lt;campo&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](/visualstudio/).  
  
Especifica la información de documentación, incluida una descripción, para un campo o un miembro que se define en un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 Nombre del campo o el miembro. Cuando el elemento `<field>` se utiliza en una función constructora, `name` es obligatorio y define el miembro al que se aplica la etiqueta. Cuando el elemento `<field>` está anotando directamente un campo, se omite este atributo y el nombre utilizado por Visual Studio es el nombre del campo real en el código fuente.  
  
 `static`  
 Opcional. Especifica si el campo es un miembro de la función constructora o un miembro del objeto devuelto por la función constructora. Establézcalo en `true` para tratar el campo como miembro de la función constructora. Establézcalo en `false` para tratar el campo como miembro del objeto devuelto por la función constructora.  
  
 `type`  
 Opcional. Tipo de datos del campo. El tipo puede ser uno de los siguientes:  
  
-   Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
-   Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
-   Una función constructora de JavaScript.  
  
 `integer`  
 Opcional. Si `type` es `Number`, especifica si el campo es un entero. Establézcalo en `true` para indicar que el campo es un entero; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `domElement`  
 Opcional. Este atributo está en desuso; el atributo `type` tiene prioridad sobre este. Este atributo especifica si el campo documentado es un elemento DOM. Establézcalo en `true` para especificar que el campo es un elemento DOM; de lo contrario, establézcalo en `false`. Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata el campo documentado como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `mayBeNull`  
 Opcional. Especifica si el campo documentado se puede establecer en NULL. Establézcalo en `true` para indicar que el campo se puede establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementType`  
 Opcional. Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
 `elementInteger`  
 Opcional. Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros. Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementDomElement`  
 Opcional. Este atributo está en desuso; el atributo `elementType` tiene prioridad sobre este. Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM. Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`. Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `elementMayBeNull`  
 Opcional. Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL. Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `helpKeyword`  
 Opcional. Palabra clave de la Ayuda de F1.  
  
 `locid`  
 Opcional. Identificador de la información de localización sobre el campo. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) etiqueta.  
  
 `value`  
 Opcional. Especifica el código que se debe evaluar para uso de IntelliSense en lugar del propio código de función. Para `<field>`, este atributo se admite para las funciones constructoras, pero no para los literales de objeto. Puede utilizar este atributo para proporcionar información de tipos cuando el tipo de campo es indefinido. Por ejemplo, puede usar `value=’1’` para tratar el tipo de campo como un número.  
  
 `description`  
 Opcional. Descripción del campo.  
  
## <a name="remarks"></a>Comentarios  
 El atributo `name` es obligatorio cuando se documenta un campo en una función constructora. Para todos los demás escenarios, todos los atributos del elemento `<field>` son opcionales.  
  
 Cuando se documenta una función constructora, el elemento `<field>` debe aparecer inmediatamente antes de la declaración de campo. El atributo `name` debe coincidir con el nombre de campo que se utiliza en el código fuente. Para los miembros de objeto, se puede omitir el atributo `name` si el elemento `<field>` aparece inmediatamente antes de la declaración de miembro de objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el elemento `<field>`.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `<field>` con el atributo `static` establecido en `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `<field>` con el atributo `static` establecido en `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `<field>` con el atributo `value`.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)



