---
title: Método includes (cadena) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637035"
---
# <a name="includes-method-string-javascript"></a>Método includes (cadena) (JavaScript)
Devuelve un valor booleano que indica si la cadena pasada se encuentra en el objeto de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. El objeto de cadena con el que se contrasta.  
  
 `substring`  
 Obligatorio. Cadena que se va a comprobar.  
  
 `position`  
 Opcional. La posición del primer carácter con el que se va a probar en el objeto de cadena, empezando por 0.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la cadena pasada se encuentra en el objeto de cadena, el método `includes` devuelve `true`; en caso contrario, devuelve `false`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]