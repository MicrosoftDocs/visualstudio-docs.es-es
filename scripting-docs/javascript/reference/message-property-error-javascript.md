---
title: Message (propiedad) (Error) (JavaScript) | Documentos de Microsoft
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
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638575"
---
# <a name="message-property-error-javascript"></a>message (Propiedad, Error de JavaScript)
Devuelve una cadena de mensaje de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Parámetros  
 `errorObj`  
 Obligatorio. Instancia de `Error` objeto.  
  
## <a name="remarks"></a>Comentarios  
 El `message` propiedad devuelve una cadena que contiene un mensaje de error asociado a un error específico.  
  
 El `description` y `message` propiedades proporcionan la misma funcionalidad. El `description` propiedad proporciona compatibilidad; el `message` propiedad cumple la norma ECMA.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se hace que se produzca una excepción TypeError y muestra el nombre del error y su mensaje.  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El resultado de este código es como sigue.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Description (propiedad) (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [name (Propiedad, Error)](../../javascript/reference/name-property-error-javascript.md)