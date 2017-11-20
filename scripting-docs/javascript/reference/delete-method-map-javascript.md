---
title: "Delete (método) (Map) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-map-javascript"></a>delete (Método, Map de JavaScript)
Quita el elemento especificado de un mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mapObj`  
 Obligatorio. Objeto `Map`.  
  
 `key`  
 Obligatorio. Clave del elemento que se va a quitar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true` si se ha eliminado el elemento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `Map` y, a continuación, elimine uno de ellos.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]