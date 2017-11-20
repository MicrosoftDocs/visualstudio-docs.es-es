---
title: WeakMap (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>WeakMap (Objeto, JavaScript)
Colección de pares clave-valor en los que cada clave es una referencia de objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Comentarios  
 Un `WeakMap` no se puede enumerar el objeto.  
  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
 En un `WeakMap` de objetos, referencias a objetos de clave se conservan "débilmente". Esto significa que `WeakMap` no impedirá que una recolección de elementos no utilizados en los objetos de clave. Cuando no hay referencias (excepto `WeakMap`) a los objetos de clave, el recolector de elementos no utilizados puede recopilar los objetos de clave.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `WeakMap`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor](../../javascript/reference/constructor-property-weakmap.md)|Especifica la función que crea un `WeakMap`.|  
|[prototipo](../../javascript/reference/prototype-property-weakmap.md)|Devuelve una referencia al prototipo para una `WeakMap`.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `WeakMap`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Quita todos los elementos de una clase `WeakMap`.|  
|[eliminar](../../javascript/reference/delete-method-weakmap-javascript.md)|Quita un elemento especificado de un `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Devuelve un elemento especificado de un `WeakMap`.|  
|[tiene](../../javascript/reference/has-method-weakmap-javascript.md)|Devuelve `true` si la `WeakMap` contiene un elemento especificado.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Agrega un nuevo elemento a un `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Devuelve una representación de cadena de un `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `WeakMap` del objeto y, a continuación, recuperarlos.  
  
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