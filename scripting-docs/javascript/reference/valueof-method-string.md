---
title: valueOf (método, String) | Documentos de Microsoft
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
ms.assetid: dfb55e6b-e38f-4b49-8196-9693f87126a4
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15fe978fb0628c046f369f565bb464353f1e6812
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640155"
---
# <a name="valueof-method-string"></a>valueOf (Método, String)
Devuelve la cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
string.valueOf()  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no tiene parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de cadena.  
  
## <a name="remarks"></a>Comentarios  
 En el ejemplo siguiente, el objeto de cadena es el mismo que el valor devuelto.  
  
```JavaScript  
var str = "every good boy does fine";  
var strStr = str.valueOf();  
  
if (str === strStr)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]