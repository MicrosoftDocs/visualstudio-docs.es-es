---
title: indexOf (método, String) (JavaScript) | Documentos de Microsoft
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
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637655"
---
# <a name="indexof-method-string-javascript"></a>indexOf (Método, String de JavaScript)
Devuelve la posición de la primera repetición de una subcadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Parámetros  
 `strObj`  
 Obligatorio. Un `String` objeto o literal de cadena.  
  
 `subString`  
 Obligatorio. La subcadena que se va a buscar en la cadena.  
  
 `startIndex`  
 Opcional. Índice en el que va a comenzar la búsqueda del objeto `String`. Si se omite, la búsqueda comienza al principio de la cadena.  
  
## <a name="remarks"></a>Comentarios  
 El **indexOf** método devuelve el principio de la subcadena en la `String` objeto. Si la subcadena no se encuentra, se devuelve -1.  
  
 Si `startindex` es negativo, `startindex` se trata como cero. Si es mayor que el índice más alto, se trata como el índice más alto.  
  
 La búsqueda se realiza de izquierda a derecha. En caso contrario, este método es idéntico a **lastIndexOf**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **indexOf** método.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [lastIndexOf (método, String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)