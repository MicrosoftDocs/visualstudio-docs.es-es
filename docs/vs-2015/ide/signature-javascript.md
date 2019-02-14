---
title: '&lt;signature&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02a4c36f3969ca0f9ef61e817afb82eb8247f041
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780322"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agrupa un conjunto de elementos relacionados para que una función o un método ofrezca documentación para las funciones sobrecargadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parámetros  
 `externalid`  
 Opcional. Si el `format` atributo para el [ \<loc >](../ide/loc-javascript.md) es elemento `vsdoc`, este atributo especifica el identificador de miembro utilizado para buscar el código XML que está asociado con la firma. A diferencia del atributo `locid`, este atributo especifica que se deben cargar todos los elementos del miembro que tiene este identificador. Cualquier información de descripción asociada presente en el código XML también se combinará con los elementos especificados en la signatura. Esto permite especificar elementos adicionales, como `<capability>`, en el archivo asociado sin especificarlos en el archivo de código fuente. `externalid` es un atributo opcional.  
  
 `externalFile`  
 Opcional. Especifica el nombre del archivo en el que se va a buscar `externalid`. Este atributo se omite si no hay ningún `externalid` presente. Es un atributo opcional. El valor predeterminado es el nombre del archivo actual, pero con una extensión .xml en lugar de .js. De forma predeterminada, para buscar el archivo se utilizan las reglas de búsqueda de recursos administrados para la localización.  
  
 `helpKeyword`  
 Opcional. Palabra clave de la Ayuda de F1.  
  
 `locid`  
 Opcional. Identificador de la información de localización sobre el campo. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) etiqueta.  
  
## <a name="remarks"></a>Comentarios  
 Utilice un elemento `<signature>` para cada descripción de función sobrecargada del archivo .js o utilice un elemento `<signature>` para cada identificador de miembro externo especificado.  
  
 El elemento `<signature>` debe colocarse en el cuerpo de la función antes de cualquier instrucción. Cuando se usa [ \<resumen >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), o [ \<devuelve >](../ide/returns-javascript.md) elementos con el `<signature>` elemento, Coloque los demás elementos dentro de la `<signature>` bloque.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el elemento `<signature>`.  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
