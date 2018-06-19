---
title: establecer (método, Map) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639435"
---
# <a name="set-method-map-javascript"></a>set (Método, Map de JavaScript)
Agrega un nuevo elemento a un mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mapObj`  
 Obligatorio. Objeto `Map`.  
  
 `key`  
 Obligatorio. Clave del nuevo elemento.  
  
 `value`  
 Obligatorio. Valor del elemento que se va a agregar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Devuelve el objeto `Map` que contiene los nuevos pares clave-valor.  
  
## <a name="remarks"></a>Comentarios  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Map` y después recuperarlos.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]