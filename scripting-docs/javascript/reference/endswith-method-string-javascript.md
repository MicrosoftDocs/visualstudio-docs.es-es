---
title: "endsWith (método, String) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="endswith-method-string-javascript"></a>Método endsWith (cadena) (JavaScript)
Devuelve un valor que indica si una cadena o subcadena finaliza con otra cadena especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. Objeto de cadena con el que se va a buscar.  
  
 `str`  
 Obligatorio. La cadena de búsqueda.  
  
 `position`  
 Opcional. La posición del primer carácter con el que se va a buscar en el objeto de cadena, empezando por 0.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la cadena que empieza en `position` finaliza con la cadena de búsqueda, el método `endsWith` devuelve `true`; en caso contrario, devuelve `false`.  
  
## <a name="exceptions"></a>Excepciones  
 Si `str` es `RegExp`, se produce `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]