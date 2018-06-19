---
title: prototype (propiedad) (cadena) | Documentos de Microsoft
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639185"
---
# <a name="prototype-property-string"></a>prototype (Propiedad, String)
Devuelve una referencia al prototipo correspondiente a una clase de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `string` argumento es el nombre de una cadena.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método a la `String` que devuelve el valor del último elemento de la cadena del objeto, declare la función, agréguela a `String.prototype`y, a continuación, usarla.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos tienen un `prototype` propiedad que es de solo lectura. Pueden agregar propiedades y métodos al prototipo, pero el objeto no puede asignarse a otro prototipo. Sin embargo, los objetos definidos por el usuario es posible asignar un nuevo prototipo.  
  
 Las listas de métodos y propiedades para cada objeto intrínseco en esta referencia del lenguaje indican que son parte del prototipo del objeto, y cuáles no.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]