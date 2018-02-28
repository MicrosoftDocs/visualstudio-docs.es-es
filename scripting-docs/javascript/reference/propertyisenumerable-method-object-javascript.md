---
title: "propertyIsEnumerable (método) (objeto) (JavaScript) | Documentos de Microsoft"
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
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable (Método, Object de JavaScript)
Determina si una propiedad especificada es enumerable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Instancia de un objeto.  
  
 `proName`  
 Obligatorio. Valor de cadena de un nombre de propiedad.  
  
## <a name="remarks"></a>Comentarios  
 El `propertyIsEnumerable` método `true` si `proName` existe en `object` y se puede enumerar con un `For` bucle. El `propertyIsEnumerable` método `false` si `object` no tiene una propiedad del nombre especificado o si la propiedad especificada no es enumerable. Normalmente, las propiedades predefinidas no son enumerables, pero las propiedades definidas por el usuario se pueden enumerables siempre.  
  
 El `propertyIsEnumerable` método no tiene en cuenta los objetos de la cadena de prototipo.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)