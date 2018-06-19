---
title: prototype (propiedad) (Error) | Documentos de Microsoft
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639485"
---
# <a name="prototype-property-error"></a>prototype (Propiedad, Error)
Devuelve una referencia al prototipo correspondiente a un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `error` argumento es el nombre de un error.  
  
 Use la `prototype` propiedad para proporcionar un conjunto básico de funcionalidad a un Error. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Error` que devuelva el valor del elemento más grande de la matriz, declare la función, agréguela a `Error.prototype` y después úsela.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos tienen un `prototype` propiedad que es de solo lectura. Pueden agregar propiedades y métodos al prototipo, pero el objeto no puede asignarse a otro prototipo. Sin embargo, los objetos definidos por el usuario es posible asignar un nuevo prototipo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]