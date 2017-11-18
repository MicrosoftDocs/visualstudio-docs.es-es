---
title: "Función Object.getOwnPropertySymbols (JavaScript) | Documentos de Microsoft"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Función Object.getOwnPropertySymbols (JavaScript)
Devuelve las propiedades de símbolos propios de un objeto. Las propiedades de símbolos propios de un objeto son aquellas que se definen directamente en ese objeto y que no se heredan del prototipo del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que contiene los símbolos propios.  
  
## <a name="return-value"></a>Valor devuelto  
 Matriz que contiene los símbolos propios del objeto.  
  
## <a name="remarks"></a>Comentarios  
 Deberá usar `Object.getOwnPropertySymbols` para obtener las propiedades de símbolo de un objeto. `Object.getOwnPropertyNames` no devolverá las propiedades de símbolo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo obtener las propiedades de símbolo de un objeto.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]