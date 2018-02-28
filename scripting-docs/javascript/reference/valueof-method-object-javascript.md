---
title: "valueOf (método) (objeto) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>valueOf (Método, Object de JavaScript)
Devuelve el valor primitivo del objeto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `object` referencia es cualquier intrínseca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
 El `valueOf` método se define de forma diferente para cada función intrínseca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
|Objeto|Valor devuelto|  
|------------|------------------|  
|Matriz|Devuelve la instancia de matriz.|  
|Booleano|El valor booleano.|  
|Fecha|El valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC.|  
|Función|La propia función.|  
|Número|Valor numérico.|  
|Objeto|El propio objeto. Este es el valor predeterminado.|  
|String|Valor de cadena.|  
  
 El **matemáticas** y `Error` objetos no tienen un `valueOf` método.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Se aplica a**: [objeto Array](../../javascript/reference/array-object-javascript.md)&#124; [Boolean (objeto)](../../javascript/reference/boolean-object-javascript.md)&#124; [Fecha objeto](../../javascript/reference/date-object-javascript.md)&#124; [Función objeto](../../javascript/reference/function-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)&#124; [Objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toString (Método, Object)](../../javascript/reference/tostring-method-object-javascript.md)