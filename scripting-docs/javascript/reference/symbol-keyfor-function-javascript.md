---
title: Función Symbol.keyFor (JavaScript) | Documentos de Microsoft
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
ms.assetid: f0b6f034-6d0a-421c-b1c6-52489411e9a3
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22f671a1ea14ce56c52fccbce75893516a10bcc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639535"
---
# <a name="symbolkeyfor-function-javascript"></a>Función Symbol.keyFor (JavaScript)
Devuelve la clave de un símbolo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Symbol.keyFor(sym);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sym`  
 Obligatorio. El objeto de símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Este método busca el símbolo en el registro de símbolos globales.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Local symbol  
var sym1 = Symbol("desc");  
// Global symbol  
var sym2 = Symbol.for("desc");  
  
console.log(Symbol.keyFor(sym1)):  
console.log(Symbol.keyFor(sym2));  
  
// Output:  
// undefined  
// desc  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]