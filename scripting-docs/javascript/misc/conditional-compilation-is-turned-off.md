---
title: Compilación condicional está desactiva | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092890"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilación condicional está desactiva
Se intentó utilizar una variable de compilación condicional sin la primera compilación condicional de activación en. Activar la compilación condicional indica la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilador para interpretar los identificadores que comiencen con como variables de compilación condicional. Para ello a partir de su código con la instrucción condicional:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue la siguiente instrucción al principio del código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on instrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if instrucción](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)