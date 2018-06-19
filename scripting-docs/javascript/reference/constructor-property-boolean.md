---
title: constructor (propiedad) (booleano) | Documentos de Microsoft
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636015"
---
# <a name="constructor-property-boolean"></a>constructor (Propiedad, Boolean)
Especifica la función que crea un valor booleano.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `boolean`  
 El nombre del valor booleano.  
  
 `value`  
 Opcional. Especifica el valor booleano. Puede tratarse de los números 1 ó 0, o la cadena "true" o "false".  
  
## <a name="remarks"></a>Comentarios  
 El `constructor` propiedad contiene una referencia a la función que crea instancias del objeto booleano.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad de constructor.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]