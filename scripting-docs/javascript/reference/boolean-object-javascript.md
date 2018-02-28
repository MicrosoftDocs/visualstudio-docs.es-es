---
title: Boolean (objeto) (JavaScript) | Documentos de Microsoft
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
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Boolean (Objeto de JavaScript)
Crea un nuevo valor booleano.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Parámetros  
 `boolObj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Boolean`.  
  
 `boolValue`  
 Opcional. El valor booleano inicial para el nuevo objeto. Si `boolvalue` se omite o es `false`(0) `null`, `NaN`, o una cadena vacía, el valor inicial del objeto Boolean es `false`. En caso contrario, el valor inicial es `true`.  
  
## <a name="remarks"></a>Comentarios  
 La `Boolean` objeto es un contenedor para el tipo de datos Boolean. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]utiliza implícitamente el `Boolean` objeto siempre que sea un tipo de datos booleano se convierte en un `Boolean` objeto.  
  
 Rara vez crear instancias del `Boolean` objeto explícitamente.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Boolean`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor (propiedad)](../../javascript/reference/constructor-property-boolean.md)|Especifica la función que crea un valor booleano.|  
|[prototype (propiedad)](../../javascript/reference/prototype-property-boolean.md)|Devuelve una referencia al prototipo para un booleano.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Boolean`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[toString (método)](../../javascript/reference/tostring-method-boolean-1.md)|Devuelve una representación de cadena de un valor booleano.|  
|[valueOf (método)](../../javascript/reference/valueof-method-boolean.md)|Obtiene una referencia para el valor booleano.|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]