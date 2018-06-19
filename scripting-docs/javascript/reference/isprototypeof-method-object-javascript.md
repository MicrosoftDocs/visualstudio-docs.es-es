---
title: isPrototypeOf (método) (objeto) (JavaScript) | Documentos de Microsoft
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
- isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637385"
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf (Método, Object de JavaScript)
Determina si un objeto existe en la cadena de prototipo de otro objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Parámetros  
 `prototype`  
 Obligatorio. Prototipo del objeto.  
  
 `object`  
 Obligatorio. Otro objeto cuya cadena de prototipo se va a comprobar.  
  
## <a name="remarks"></a>Comentarios  
 El método `isPrototypeOf` devuelve `true` si `object` tiene `prototype` en su cadena de prototipo. La cadena de prototipo se utiliza para compartir la funcionalidad entre instancias del mismo tipo de objetos. El método `isPrototypeOf` devuelve `false` cuando `object` no es un objeto o cuando `prototype` no aparece en la cadena de prototipo de `object`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `isPrototypeOf`.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)