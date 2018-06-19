---
title: valueOf (método, Array) | Documentos de Microsoft
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68dc5599a495df42629ec49f25e8f5344f67e3d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640535"
---
# <a name="valueof-method-array"></a>valueOf (Método, Array)
Devuelve el valor primitivo del objeto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array.valueOf()  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no tiene parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la instancia de matriz.  
  
## <a name="remarks"></a>Comentarios  
 En el ejemplo siguiente, el objeto de matriz de instancias es el mismo que el valor devuelto de este método.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]