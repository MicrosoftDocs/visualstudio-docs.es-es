---
title: Compilación condicional está desactiva | Documentos de Microsoft
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
ms.openlocfilehash: 8317121b840d82ab12d4a9e1ca50f6680eb1e21d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946581"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilación condicional está desactiva
Se intentó utilizar una variable de compilación condicional sin la primera compilación condicional de activación en. Activar la compilación condicional indica la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilador para interpretar los identificadores que comiencen con como variables de compilación condicional. Para ello a partir de su código con la instrucción condicional:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue la siguiente instrucción al principio del código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on instrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if instrucción](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)