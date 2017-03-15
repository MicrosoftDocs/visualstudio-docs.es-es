---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "etiqueta XML JavaScript <field>"
  - "field (etiqueta XML) [JavaScript]"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la información de documentación, incluida una descripción, para un campo o un miembro que se define en un objeto.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `name`  
 Nombre del campo o el miembro.  Cuando el elemento `<field>` se utiliza en una función constructora, `name` es obligatorio y define el miembro al que se aplica la etiqueta.  Cuando el elemento `<field>` está anotando directamente un campo, se omite este atributo y el nombre utilizado por Visual Studio es el nombre del campo real en el código fuente.  
  
 `static`  
 Opcional.  Especifica si el campo es un miembro de la función constructora o un miembro del objeto devuelto por la función constructora.  Establézcalo en `true` para tratar el campo como miembro de la función constructora.  Establézcalo en `false` para tratar el campo como miembro del objeto devuelto por la función constructora.  
  
 `type`  
 Opcional.  Tipo de datos del campo.  El tipo puede ser uno de los siguientes:  
  
-   Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
-   Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
-   Una función constructora de JavaScript.  
  
 `integer`  
 Opcional.  Si `type` es `Number`, especifica si el campo es un entero.  Establézcalo en `true` para indicar que el campo es un entero; de lo contrario, establézcalo en `false`.  Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `domElement`  
 Opcional.  Este atributo está desusado; el atributo `type` tiene prioridad sobre este.  Este atributo especifica si el campo documentado es un elemento DOM.  Establézcalo en `true` para especificar que el campo es un elemento DOM; de lo contrario, establézcalo en `false`.  Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata el campo documentado como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `mayBeNull`  
 Opcional.  Especifica si el campo documentado se puede establecer en NULL.  Establézcalo en `true` para indicar que el campo se puede establecer en NULL; de lo contrario, establézcalo en `false`.  El valor predeterminado es `false`.  Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementType`  
 Opcional.  Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
 `elementInteger`  
 Opcional.  Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros.  Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`.  Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Este atributo está desusado; el atributo `elementType` tiene prioridad sobre este.  Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM.  Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`.  Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
 `elementMayBeNull`  
 Opcional.  Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL.  Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`.  El valor predeterminado es `false`.  Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
 `helpKeyword`  
 Opcional.  Palabra clave de la Ayuda de F1.  
  
 `locid`  
 Opcional.  Identificador de la información de localización sobre el campo.  El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax.  El tipo de identificador depende del formato especificado en la etiqueta [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Opcional.  Especifica el código que se debe evaluar para uso de IntelliSense en lugar del propio código de función.  Para `<field>`, este atributo se admite para las funciones constructoras, pero no para los literales de objeto.  Puede utilizar este atributo para proporcionar información de tipos cuando el tipo de campo es indefinido.  Por ejemplo, puede utilizar `value=’1’` para tratar el tipo de campo como un número.  
  
 `description`  
 Opcional.  Descripción del campo.  
  
## Comentarios  
 El atributo `name` es obligatorio cuando se documenta un campo en una función constructora.  Para todos los demás escenarios, todos los atributos del elemento `<field>` son opcionales.  
  
 Cuando se documenta una función constructora, el elemento `<field>` debe aparecer inmediatamente antes de la declaración de campo.  El atributo `name` debe coincidir con el nombre de campo que se utiliza en el código fuente.  Para los miembros de objeto, se puede omitir el atributo `name` si el elemento `<field>` aparece inmediatamente antes de la declaración de miembro de objeto.  
  
## Ejemplo  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `<field>` con el atributo `static` establecido en `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## Ejemplo  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `<field>` con el atributo `value`.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)