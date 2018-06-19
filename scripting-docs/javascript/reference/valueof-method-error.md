---
title: valueOf (método) (Error) | Documentos de Microsoft
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640205"
---
# <a name="valueof-method-error"></a>valueOf (Método, Error)
Devuelve el valor de cadena de un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>Parámetros  
 La `error` objeto es cualquier instancia de un Error.  
  
## <a name="return-value"></a>Valor devuelto  
 La cadena "Error:" junto con el mensaje de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `valueOF` método con una fecha.  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]