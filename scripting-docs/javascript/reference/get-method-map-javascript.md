---
title: "Get (método) (Map) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>get (Método, Map de JavaScript)
Devuelve un elemento especificado de un mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mapObj`  
 Obligatorio. Objeto `Map`.  
  
 `key`  
 Obligatorio. La clave de un elemento en el `Map`.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Devuelve el objeto asociado a la clave. Si el `Map` no contiene la clave, este método devuelve un `undefined` valor.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un elemento de un `Map` objeto.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]