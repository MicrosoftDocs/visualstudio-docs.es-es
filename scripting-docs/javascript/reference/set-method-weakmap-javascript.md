---
title: establecer (método, WeakMap) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639605"
---
# <a name="set-method-weakmap-javascript"></a>set (Método, WeakMap de JavaScript)
Agrega un nuevo elemento a un objeto `WeakMap`.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `weakmapObj`  
 Obligatorio. Objeto `WeakMap`.  
  
 `key`  
 Obligatorio. Objeto que representa la clave del elemento que se va a agregar. Debe ser una referencia de objeto.  
  
 `value`  
 Obligatorio. Valor del elemento que se va a agregar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Devuelve el objeto `WeakMap` que contiene los nuevos pares clave-valor.  
  
## <a name="remarks"></a>Comentarios  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra la forma de agregar miembros a un objeto `WeakMap`.  
  
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
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]