---
title: "tiene (método, Map) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-map-javascript"></a>has (Método, Map de JavaScript)
Devuelve `true` si la asignación contiene el elemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mapObj`  
 Obligatorio. Objeto `Map`.  
  
 `key`  
 Obligatorio. Clave del elemento que se va a probar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true`Si el objeto map contiene el elemento especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un miembro a un `Map` y, a continuación, compruebe si la asignación lo contiene.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]