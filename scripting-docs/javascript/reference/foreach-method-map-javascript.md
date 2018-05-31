---
title: forEach (método, Map) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7d625fb4dfe88b2db69e6aa0ff66c7e90f66
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335806"
---
# <a name="foreach-method-map-javascript"></a>forEach (Método, Map de JavaScript)
Realiza la acción especificada para cada elemento de un mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mapObj`  
 Requerido. Un objeto `Map`.  
  
 `callbackfn`  
 Requerido. La función que `forEach` llama una vez para cada elemento en el mapa. `callbackfn` acepta hasta tres argumentos. `forEach` llamadas a la `callbackfn` funcionar una vez por cada elemento del mapa.  
  
 `thisArg`  
 Opcional. Un objeto que la `this` palabra clave puede hacer referencia a en el `callbackfn` (función). Si se omite `thisArg`, se usa `undefined` como valor `this`.  
  
## <a name="exceptions"></a>Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Puede declarar la función de devolución de llamada usando hasta tres parámetros, tal como se muestra en la tabla siguiente.  
  
|Argumento de devolución de llamada|de esquema JSON|  
|-----------------------|----------------|  
|`value`|Un valor contenido en el mapa.|  
|`key`|Una clave contenida en el mapa.|  
|`mapObj`|La `Map` objeto atravesar.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar los miembros de un `Map` con `forEach`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
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
