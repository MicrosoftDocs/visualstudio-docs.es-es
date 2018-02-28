---
title: Name (propiedad) (Error) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>name (Propiedad, Error de JavaScript)
Devuelve el nombre de un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Parámetros  
 `errorObj`  
 Obligatorio. Instancia de `Error` objeto.  
  
## <a name="remarks"></a>Comentarios  
 El **nombre** propiedad devuelve el tipo de nombre o de una excepción de error. Cuando se produce un error en tiempo de ejecución, la propiedad name se establece en uno de los siguientes tipos de excepción nativos:  
  
|Tipo de excepción|Significado|  
|--------------------|-------------|  
|ConversionError|Este error se produce cuando hay un intento para convertir un objeto en algo que no se puede convertir.|  
|RangeError|Este error se produce cuando se proporciona una función con un argumento que ha superado su intervalo permitido. Por ejemplo, este error se produce si intenta construir una `Array` objeto con una longitud que no es un entero positivo válido.|  
|ReferenceError|Este error se produce cuando se ha detectado una referencia no válida. Por ejemplo, este error se producirá si una referencia esperada es `null`.|  
|RegExpError|Este error se produce cuando se produce un error de compilación con una expresión regular. Una vez compilada la expresión regular, sin embargo, no puede producirse este error. En este ejemplo se producirá, por ejemplo, cuando una expresión regular se declara con un modelo que tiene una sintaxis no válida, o distinto de **i**, **g**, o **m**, o si contiene el mismo indicador más de una vez.|  
|SyntaxError|Este error se produce cuando se analiza el texto de origen y del texto de origen que no cumple la sintaxis correcta. Este error se producirá, por ejemplo, si la `eval` función se llama con un argumento que no sea texto de programa válido.|  
|TypeError|Este error se produce cuando el tipo real de un operando no coincide con el tipo esperado. Un ejemplo de cuándo se produce este error es una llamada de función realizada sobre algo que no es un objeto o no admite la llamada.|  
|URIError|Este error se produce cuando se detecta un indicador de recursos uniformes (URI). Por ejemplo, se trata de error se produce cuando se encuentra un carácter no válido en una cadena que se va a codificar o descodificar.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se hace que se produzca una excepción TypeError y muestra el nombre del error y su mensaje.  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El resultado de este código es como sigue.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Description (propiedad) (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Message (propiedad) (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [number (Propiedad, Error)](../../javascript/reference/number-property-error-javascript.md)