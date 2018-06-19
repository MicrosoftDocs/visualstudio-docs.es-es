---
title: tiene (método, WeakMap) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636695"
---
# <a name="has-method-weakmap-javascript"></a>has (Método, WeakMap de JavaScript)
Devuelve `true` si la `WeakMap` objeto contiene el elemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `weakmapObj`  
 Obligatorio. Objeto `WeakMap`.  
  
 `key`  
 Obligatorio. Clave del elemento que se va a probar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true`Si el `WeakMap` contiene la clave especificada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un miembro a un `WeakMap` y, a continuación, usar `has` para comprobar si está presente.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]