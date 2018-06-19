---
title: Number (propiedad, Error) (JavaScript) | Documentos de Microsoft
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639105"
---
# <a name="number-property-error-javascript"></a>number (Propiedad, Error de JavaScript)
Devuelve o establece el valor numérico asociado a un error específico. El `Error` es la propiedad predeterminada del objeto **número**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Parámetros  
 *Objeto*  
 Cualquier instancia de la `Error` objeto.  
  
 *errorNumber*  
 Un entero que representa un error.  
  
## <a name="remarks"></a>Comentarios  
 Un número de error es un valor de 32 bits. La palabra de 16 bits superior es el código de componente y la palabra inferior es el código de error. Para determinar el código de error, use la `&` (bit a bit y) para combinar la propiedad number con el número hexadecimal `0xFFFF`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se hace que se produzca una excepción y muestra el código de error que se deriva del número de error.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Ejemplo  
 El resultado de este código es como sigue.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Description (propiedad) (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Message (propiedad) (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name (Propiedad, Error)](../../javascript/reference/name-property-error-javascript.md)