---
title: Esta instrucción (JavaScript) | Documentos de Microsoft
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
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640325"
---
# <a name="this-statement-javascript"></a>this (Instrucción de JavaScript)
Hace referencia al objeto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento `property` obligatorio es una de las propiedades del objeto actual.  
  
 La palabra clave `this` se puede utilizar generalmente en constructores de objetos para hacer referencia al objeto actual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, **esto** hace referencia al objeto Car recién creado y asigna valores a tres propiedades:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 El **esto** palabra clave suele hacer referencia a la **ventana** objeto si se usa fuera del ámbito de cualquier otro objeto. Sin embargo, dentro de los controladores de eventos `this` hace referencia al elemento DOM que provocó el evento.  
  
 En el código siguiente (para Internet Explorer 9 o posterior), el controlador de eventos imprime la versión de cadena de un botón que tiene un identificador de "clicker".  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Uso del método bind](../../javascript/advanced/using-the-bind-method-javascript.md)