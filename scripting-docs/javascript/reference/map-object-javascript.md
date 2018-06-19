---
title: Map (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639295"
---
# <a name="map-object-javascript"></a>Map (Objeto, JavaScript)
Colección de pares clave-valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Comentarios  
 Las claves y los valores de la colección pueden ser de cualquier tipo. Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Map`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor](../../javascript/reference/constructor-property-map.md)|Especifica la función que crea un mapa.|  
|[prototipo](../../javascript/reference/prototype-property-map.md)|Devuelve una referencia al prototipo correspondiente a un mapa.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Devuelve el número de elementos en un mapa.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Map`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Quita todos los elementos de un mapa.|  
|[eliminar](../../javascript/reference/delete-method-map-javascript.md)|Quita un elemento especificado de un mapa.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Realiza la acción especificada para cada elemento de un mapa.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Devuelve un elemento especificado de un mapa.|  
|[tiene](../../javascript/reference/has-method-map-javascript.md)|Devuelve `true` si el mapa contiene un elemento especificado.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Agrega un nuevo elemento a un mapa.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Devuelve una representación de cadena de un mapa.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Map` y después recuperarlos.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]