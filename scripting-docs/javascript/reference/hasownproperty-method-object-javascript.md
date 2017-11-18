---
title: "hasOwnProperty (método) (objeto) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty (Método, Object de JavaScript)
Determina si un objeto tiene una propiedad con el nombre especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Instancia de un objeto.  
  
 `proName`  
 Obligatorio. Valor de cadena de un nombre de propiedad.  
  
## <a name="remarks"></a>Comentarios  
 El `hasOwnProperty` método `true` si `object` tiene una propiedad del nombre especificado, `false` si no es así. Este método no comprueba las propiedades de cadena de prototipo del objeto; la propiedad debe ser miembro del propio objeto.  
  
 Esta propiedad no se admite en objetos host para Internet Explorer 8 y niveles inferiores.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, todos los `String` objetos comparten un método split común. El código siguiente mostrará **false** y **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [In (Operador)](../../javascript/reference/in-operator-decrementjavascript.md)