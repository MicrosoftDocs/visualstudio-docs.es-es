---
title: undefined (constante de JavaScript) | Documentos de Microsoft
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
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640525"
---
# <a name="undefined-constant-javascript"></a>undefined (Constante de JavaScript)
Un valor que nunca se ha definido, por ejemplo, una variable que no se ha inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Comentarios  
 El `undefined` constante es un miembro de la `Global` de objetos y está disponible cuando se inicializa el motor de scripting. Si una variable se ha declarado pero no inicializado, su valor es **indefinido**.  
  
 Si no se ha declarado una variable, no se pueden comparar a `undefined`, pero se puede comparar el tipo de la variable en la cadena "undefined".  
  
 El `undefined` constante es útil cuando explícitamente pruebas o establecer una variable en sin definir.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `undefined` constante.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Requisitos  
 El `undefined` propiedad se introdujo en [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]y se ha realizado de solo lectura en [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [typeof (Operador)](../../javascript/reference/typeof-operator-decrementjavascript.md)