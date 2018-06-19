---
title: pila (propiedad, Error) (JavaScript) | Documentos de Microsoft
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641145"
---
# <a name="stack-property-error-javascript"></a>stack (Propiedad, Error de JavaScript)
Obtiene o establece la pila de errores como una cadena que contiene los marcos del seguimiento de la pila.   
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Comentarios  
 La propiedad `stack` se establece en `undefined` cuando se construye el error y obtiene la información de seguimiento cuando se produce el error. Si un error se repite, la propiedad `stack` se actualiza cada vez que se produce el error.  
  
 Marcos de pila se muestran en el siguiente formato: **at nombrefunción (\<nombre completo/URL >:\<número de línea >:\<número de columna >)**  
  
 Si crea su propio objeto de error y establece el seguimiento de la pila en un valor, el valor no se sobrescribirá cuando se produzca el error.  
  
 La propiedad `stack` no muestra las funciones inline en sus marcos, solo muestra la pila física.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener la pila cuando se detecta un error.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer y luego obtener la pila.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Description (propiedad) (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Message (propiedad) (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Name (propiedad) (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit (Propiedad, Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)