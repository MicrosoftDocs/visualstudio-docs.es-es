---
title: toString (método) 1 (booleano) | Documentos de Microsoft
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640345"
---
# <a name="tostring-method-boolean-1"></a>toString (método) (booleano) 1
Devuelve una representación de cadena de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>Parámetros  
 `boolean`  
 Obligatorio. Objeto para el que se va a obtener una representación de cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el valor booleano es `true`, devuelve "true". En caso contrario, devuelve "false".  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **toString** método.  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]