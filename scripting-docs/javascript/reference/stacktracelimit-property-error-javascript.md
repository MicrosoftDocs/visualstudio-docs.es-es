---
title: stacktracelimit propiedad, (Error) (JavaScript) | Documentos de Microsoft
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
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640575"
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit (Propiedad, Error de JavaScript)
Obtiene o establece el límite de seguimiento de pila, que es equivalente al número de fotogramas de error para mostrar. El límite predeterminado es 10.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Comentarios  
 Puede establecer la `stackTraceLimit` propiedad en cualquier valor positivo entre 0 y `Infinity`. Si el `stackTraceLimit` propiedad está establecida en 0 en el momento en que se produce un error, no se muestra ningún seguimiento de pila. Si la propiedad se establece en un valor negativo o un valor no numérico, el valor se convierte en 0. Si se establece la stackTraceLimit en `Infinity`, se muestra la pila completa. En caso contrario, `ToUint32` se usa para convertir el valor.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer y, a continuación, obtener el límite de seguimiento de pila.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 En Internet Explorer 10 y admiten [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicaciones.  
  
 **Se aplica a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Description (propiedad) (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Message (propiedad) (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Name (propiedad) (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [stack (Propiedad, Error)](../../javascript/reference/stack-property-error-javascript.md)