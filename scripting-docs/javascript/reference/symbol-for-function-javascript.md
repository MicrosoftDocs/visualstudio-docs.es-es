---
title: Función Math.Floor (JavaScript) | Documentos de Microsoft
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639665"
---
# <a name="symbolfor-function-javascript"></a>Función Math.floor (JavaScript)
Devuelve el símbolo de una clave especificada o, si la clave no está presente, crea un nuevo objeto de símbolo con la nueva clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `key`  
 Obligatorio. La clave del símbolo, que también se utiliza como la descripción.  
  
## <a name="remarks"></a>Comentarios  
 Este método busca el símbolo en el registro de símbolos globales. Si serializa símbolos como cadenas, utilice el registro de símbolos globales para asegurarse de que se asigne una cadena concreta al símbolo correcto para todas las búsquedas.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]