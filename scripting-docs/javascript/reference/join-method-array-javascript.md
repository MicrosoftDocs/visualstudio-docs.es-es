---
title: Join (método, Array) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637615"
---
# <a name="join-method-array-javascript"></a>join (Método, Array de JavaScript)
Agrega todos los elementos de una matriz separados por la cadena de separador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Un objeto `Array`.  
  
 `separator`  
 Opcional. Una cadena utilizada para separar un elemento de una matriz del siguiente en el cuadro `String`. Si se omite, los elementos de matriz se separan con una coma.  
  
## <a name="remarks"></a>Comentarios  
 Si algún elemento de la matriz es **indefinido** o `null`, se trata como una cadena vacía.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **combinación** método.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)