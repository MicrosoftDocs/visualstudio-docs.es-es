---
title: La compilación condicional está desactivada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572930"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilación condicional está desactiva
Intentó usar una variable de compilación condicional sin activar primero la compilación condicional. Al activar la compilación condicional, se indica al compilador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que interprete identificadores que empiezan por @ como variables de compilación condicionales. Para ello, inicie el código condicional con la instrucción:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue la siguiente instrucción al principio del código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vea también  
   de [compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on instrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if instrucción](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)