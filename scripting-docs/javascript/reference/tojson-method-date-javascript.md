---
title: toJSON (método, Date) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641295"
---
# <a name="tojson-method-date-javascript"></a>toJSON (Método, Date de JavaScript)
Utilizado por el [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) método para permitir la transformación de datos de un objeto para la serialización de JavaScript Object Notation (JSON).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Parámetros  
 `objectname`  
 Obligatorio. Un objeto que JSON es deseable serialización.  
  
## <a name="remarks"></a>Comentarios  
 El `toJSON` método lo usa el `JSON.stringify` función. `JSON.stringify`Serializa un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor en texto JSON. Si un `toJSON` método se proporciona para `JSON.stringify`, `toJSON` se llama al método cuando `JSON.stringify` se llama.  
  
 El `toJSON` método es un miembro integrado de la [fecha](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto. Devuelve una cadena de fecha con formato ISO de la zona de horaria UTC (indicada por el sufijo Z).  
  
 Puede invalidar la `toJSON` método para el `Date` escriba, o definir una `toJSON` método para otros tipos de objeto lograr una transformación de datos para el tipo de objeto específico antes de la serialización de JSON.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el `toJSON` método para serializar los valores de miembro de cadena en mayúsculas. El `toJSON` se llama al método cuando `JSON.stringify` se llama.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `toJSON` método que es un miembro integrado de la [fecha](../../javascript/reference/date-object-javascript.md) objeto.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Se aplica a:** [objeto de fecha](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify (función)](../../javascript/reference/json-stringify-function-javascript.md)   
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)