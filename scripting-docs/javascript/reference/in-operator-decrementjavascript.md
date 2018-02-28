---
title: in (operador) (JavaScript) | Documentos de Microsoft
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="in-operator-javascript"></a>in (Operador de JavaScript)
Comprueba la existencia de una propiedad en un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Obligatorio. Cualquier variable.  
  
 `property`  
 Obligatorio. Una expresión que se evalúa como una expresión de cadena.  
  
 `object`  
 Obligatorio. Cualquier objeto.  
  
## <a name="remarks"></a>Comentarios  
 El `in` operador determina si un objeto tiene una propiedad denominada `property`. También determina si la propiedad forma parte de la cadena de prototipo del objeto. Para obtener más información sobre los prototipos de objeto, vea [prototipos y herencia de prototipos](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `in` operador:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)