---
title: Método Repeat (cadena) (JavaScript) | Documentos de Microsoft
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638715"
---
# <a name="repeat-method-string-javascript"></a>Método repeat (cadena) (JavaScript)
Devuelve un nuevo objeto de cadena con un valor igual a la cadena original repetido el número de veces especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. El objeto de cadena.  
  
 `count`  
 Obligatorio. Número de veces que se repetirá la cadena original en la cadena devuelta.  
  
## <a name="exceptions"></a>Excepciones  
 Este método produce un RangeError solo si el argumento es negativo o +Infinity.  
  
## <a name="remarks"></a>Comentarios  
 El método `repeat` concatena la cadena original con la nueva cadena el número de veces especificado por `count`.  
  
 Este método produce un error si `count` no es un número positivo menor que `Infinity`.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]