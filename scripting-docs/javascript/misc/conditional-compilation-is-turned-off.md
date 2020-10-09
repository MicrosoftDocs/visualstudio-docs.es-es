---
title: La compilación condicional está desactivada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 91e32971013d2dfcf0ee2dc901d84681522c7e89
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861649"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilación condicional está desactiva
Intentó usar una variable de compilación condicional sin activar primero la compilación condicional. Al activar la compilación condicional [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , se indica al compilador que interprete identificadores que empiezan por @ como variables de compilación condicionales. Para ello, inicie el código condicional con la instrucción:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue la siguiente instrucción al principio del código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variables de compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on Privacidad](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if Privacidad](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set Privacidad](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)