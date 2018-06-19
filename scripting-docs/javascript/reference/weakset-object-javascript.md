---
title: Objeto WeakSet (JavaScript) | Documentos de Microsoft
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641605"
---
# <a name="weakset-object-javascript"></a>Objeto WeakSet (JavaScript)
Una colección de objetos únicos de cualquier tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Comentarios  
 Si intenta agregar un objeto que no sea único a un `WeakSet`, el nuevo objeto no se agregará a la colección.  
  
 Al contrario que sucede con un `Set`, solo se pueden agregar objetos a la colección. No se pueden agregar valores arbitrarios a la colección.  
  
 En un `WeakSet` de objetos, referencias a objetos en el conjunto se conservan "débilmente". Esto significa que `WeakSet` no impedirá que se produzca una recolección de elementos no utilizados en los objetos. Cuando no hay referencias (salvo `WeakSet`) a los objetos, el recolector de elementos no utilizados puede recopilar los objetos.  
  
 `WeakSet` (o `WeakMap`) puede ser útil en algunos escenarios que impliquen el almacenamiento en caché de objetos o metadatos de objetos. Por ejemplo, los metadatos de los objetos no extensibles pueden almacenarse en un `WeakSet` o puede crear una memoria caché de imágenes de usuario mediante `WeakSet`.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `WeakSet`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|constructor|Especifica la función que crea un conjunto.|  
|prototipo|Devuelve una referencia al prototipo para un conjunto.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `WeakSet`.  
  
|Método|Descripción|  
|------------|-----------------|  
|agregar|Agrega un elemento a un conjunto.|  
|eliminar|Elimina el elemento especificado de un conjunto.|  
|has|Devuelve `true` si el conjunto contiene un elemento especificado.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo agregar miembros a un conjunto y, a continuación, verificar que se hayan agregado.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]