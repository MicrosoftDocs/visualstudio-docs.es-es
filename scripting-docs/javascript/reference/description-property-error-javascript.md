---
title: Description (propiedad) (Error) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>description (Propiedad, Error de JavaScript)
Devuelve o establece la cadena descriptiva asociada con un error específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Parámetros  
 *object*  
 Obligatorio. Cualquier instancia de un `Error` objeto.  
  
 `stringExpression`  
 Opcional. Una expresión de cadena que contiene una descripción del error.  
  
## <a name="remarks"></a>Comentarios  
 El **descripción** propiedad contiene la cadena de mensaje de error asociada a un error específico. Utilice el valor contenido en esta propiedad para avisar a un usuario un error.  
  
 El **descripción** y **mensaje** propiedades proporcionan la misma funcionalidad; el **descripción** propiedad proporciona compatibilidad con versiones anteriores; el  **mensaje** propiedad cumple la norma ECMA.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **descripción** propiedad.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Number (propiedad) (Error)](../../javascript/reference/number-property-error-javascript.md)   
 [Message (propiedad) (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name (Propiedad, Error)](../../javascript/reference/name-property-error-javascript.md)