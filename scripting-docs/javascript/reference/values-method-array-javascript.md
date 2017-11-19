---
title: "Método Values (matriz) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1a90dfd81ae8baf6590f69f0126adc97d42c20e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="values-method-array-javascript"></a>Método values (matriz) (JavaScript)
Devuelve un iterador que devuelve los valores de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
arrayObj.values();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Objeto de matriz.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo obtener los valores de una matriz.  
  
```JavaScript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]