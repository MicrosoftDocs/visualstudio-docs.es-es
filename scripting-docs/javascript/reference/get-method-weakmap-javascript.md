---
title: "Get (método, WeakMap) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-weakmap-javascript"></a>get (Método, WeakMap de JavaScript)
Devuelve un elemento especificado de un `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `weakmapObj`  
 Obligatorio. Objeto `WeakMap`.  
  
 `key`  
 Obligatorio. La clave de un elemento en el `WeakMap`.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Devuelve el objeto asociado a la clave. Si el `WeakMap` no contiene la clave, este método devuelve un `undefined` valor.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar los miembros de un `WeakMap` objeto.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]