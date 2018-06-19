---
title: Trim (método, String) (JavaScript) | Documentos de Microsoft
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
helpviewer_keywords:
- trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640735"
---
# <a name="trim-method-string-javascript"></a>trim (Método, String de JavaScript)
Quita los caracteres de espacio en blanco y de terminador de línea iniciales y finales de una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. Objeto `String` o literal de cadena. El método `trim` no modifica esta cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 Cadena original a la que se han quitado los caracteres de espacio en blanco y de terminador de línea iniciales y finales.  
  
## <a name="remarks"></a>Comentarios  
 Entre los caracteres que se quitan se incluyen: espacio, tabulador, avance de página, retorno de carro y salto de línea. Vea [caracteres especiales](../../javascript/advanced/special-characters-javascript.md) para obtener una lista completa de los espacios en blanco y línea de caracteres de terminador.  
  
 Para obtener un ejemplo que muestra cómo implementar su propio método de recorte, consulte [prototipos y herencia de prototipos](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `trim`.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Caracteres especiales](../../javascript/advanced/special-characters-javascript.md)   
 [String (objeto)](../../javascript/reference/string-object-javascript.md)   
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)