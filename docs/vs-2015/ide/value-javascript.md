---
title: '&lt;valor&gt; (JavaScript) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f88f3ae2e7442549004d2331b4517eb7fa2b5509
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914338"
---
# <a name="ltvaluegt-javascript"></a>&lt;valor&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica información de documentación de las funciones `get` y `set` para propiedades de ECMAScript 3.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Opcional. Tipo de datos de la propiedad. El tipo puede ser uno de los siguientes:  
  
- Un tipo de lenguaje ECMAScript de la especificación de ECMAScript 5, como `Number` y `Object`.  
  
- Un objeto DOM, como `HTMLElement`, `Window` y `Document`.  
  
- Una función constructora de JavaScript.  
  
  `integer`  
  Opcional. Si `type` es `Number`, especifica si la propiedad es un entero. Establézcalo en `true` para indicar que la propiedad es un entero; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `domElement`  
  Opcional. Este atributo está en desuso; el atributo `type` tiene prioridad sobre este. Este atributo especifica si la propiedad documentada es un elemento DOM. Establézcalo en `true` para especificar que la propiedad es un elemento DOM; de lo contrario, establézcalo en `false`. Si el atributo `type` no se establece y `domElement` se establece en `true`, IntelliSense trata la propiedad documentada como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `mayBeNull`  
  Opcional. Especifica si la propiedad documentada se puede establecer en NULL. Establézcalo en `true` para indicar que la propiedad se puede establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementType`  
  Opcional. Si `type` es `Array`, este atributo especifica el tipo de los elementos de la matriz.  
  
  `elementInteger`  
  Opcional. Si `type` es `Array` y `elementType` es `Number`, este atributo especifica si los elementos de la matriz son enteros. Establézcalo en `true` para indicar que los elementos de la matriz son enteros; de lo contrario, establézcalo en `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `elementDomElement`  
  Opcional. Este atributo está en desuso; el atributo `elementType` tiene prioridad sobre este. Si `type` es `Array`, este atributo especifica si los elementos de la matriz son elementos DOM. Establézcalo en `true` para especificar que los elementos son elementos DOM; de lo contrario, establézcalo en `false`. Si el atributo `elementType` no se establece y `elementDomElement` se establece en `true`, IntelliSense trata cada elemento de la matriz como `HTMLElement` al realizar la finalización de instrucciones.  
  
  `elementMayBeNull`  
  Opcional. Si `type` es `Array`, especifica si los elementos de la matriz se pueden establecer en NULL. Establézcalo en `true` para indicar que los elementos de la matriz se pueden establecer en NULL; de lo contrario, establézcalo en `false`. El valor predeterminado es `false`. Visual Studio no utiliza este atributo para proporcionar información de IntelliSense.  
  
  `locid`  
  Opcional. Identificador de la información de localización sobre la propiedad. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) elemento.  
  
  `description`  
  Opcional. Una descripción de la propiedad.  
  
## <a name="remarks"></a>Comentarios  
 Propiedades de ECMAScript 5 utilizan el [ \<resumen >](../ide/summary-javascript.md) elemento.  
  
 Utilice el elemento `<value>` inmediatamente antes de la función `get` o `set`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar el elemento `<value>` en una función `get`.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)



